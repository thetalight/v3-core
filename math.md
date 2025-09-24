

$(x_R+x_v)(y_R+y_v) = L^2$


由$xy=L^2,\frac{y}{x}=P$,可得   
$$
x=\frac{L}{\sqrt{P}} \\
y=L\sqrt{P}
$$  

<image src = "./images/1.png" width = "300px" height = "300px">

####  计算$x_v,y_v$
1. 当$x_R=0$ 
   
$$
x_v(y_R+y_v) = L^2 \\
x_v = \frac{L^2}{y_R+y_v} \\
x_v = \frac{L^2}{L\sqrt{P_B}} = \frac{L}{\sqrt{P_B}} \\
$$

2. 当$y_R=0$ 

$$
(x_R+x_v)y_v = L^2 \\
y_v = \frac{L^2}{x_R+x_v} \\
y_v = \frac{L^2}{L/\sqrt{P_A}} = L\sqrt{P_A} \\
$$


####  计算$x_A,y_B$
   1. 当 $P=P_A$时 ，$y_R=0$
   $$
      (x_A+\frac{L}{\sqrt{P_B}})L\sqrt{P_A} = L^2 \\
      x_A = \frac{L}{\sqrt{P_A}} - \frac{L}{\sqrt{P_B}} \\
   $$

   2. 当 $P=P_B$时 ，$x_R=0$
   $$
      \frac{L}{\sqrt{P_B}}(y_B+L\sqrt{P_A}) = L^2 \\
      y_B = L\sqrt{P_B}  -L\sqrt{P_A}  \\
   $$

#### Liquidity
   1. 当 $P \leq P_A$ 
    $$
      \Delta x = \frac{L}{\sqrt{P_A}} - \frac{L}{\sqrt{P_B}} \\
      L = \frac{\Delta x}{\frac{1}{\sqrt{P_A}} - \frac{1}{\sqrt{P_B}}  }
    $$

   2. 当 $P \geq P_B$
    $$
      \Delta y = L\sqrt{P_B}  -L\sqrt{P_A} \\
      L = \frac{\Delta y}{\sqrt{P_B}  -\sqrt{P_A}  }
    $$

   3. 当 $P_A < P < P_B$
    $$
       L = \frac{\Delta x}{\frac{1}{\sqrt{P}} - \frac{1}{\sqrt{P_B}}  } =\frac{\Delta y}{\sqrt{P}  -\sqrt{P_A} }
    $$
       

#### $\Delta$ Liquidity
   1. 当 $P \leq P_A$ 
    $$
        L_0 = \frac{x}{\frac{1}{\sqrt{P_A}} - \frac{1}{\sqrt{P_B}}}  \\
         L_1 = \frac{x + \Delta x}{\frac{1}{\sqrt{P_A}} - \frac{1}{\sqrt{P_B}}  } \\
         \Delta L=L_1-L_0 = \frac{\Delta x}{\frac{1}{\sqrt{P_A}} - \frac{1}{\sqrt{P_B}}  }
    $$

   2. 当 $P \geq P_B$
    $$
        L_0 = \frac{y}{\sqrt{P_B}  -\sqrt{P_A}  } \\
         L_1 = \frac{y + \Delta y}{\sqrt{P_B}  -\sqrt{P_A}  } \\
         \Delta L=L_1-L_0 = \frac{\Delta y}{\sqrt{P_B}  -\sqrt{P_A}  }
    $$

   3. 当 $P_A < P < P_B$
    $$
        L_0 =  \frac{x}{\frac{1}{\sqrt{P}} - \frac{1}{\sqrt{P_B}}} = \frac{y}{\sqrt{P}  -\sqrt{P_A}  }  \\
         L_1 =  \frac{x + \Delta x}{\frac{1}{\sqrt{P}} - \frac{1}{\sqrt{P_B}}} = \frac{y + \Delta y}{\sqrt{P}  -\sqrt{P_A}  } \\
         \Delta L=L_1-L_0 =\frac{\Delta x}{\frac{1}{\sqrt{P}} - \frac{1}{\sqrt{P_B}}  }= \frac{\Delta y}{\sqrt{P}  -\sqrt{P_A}  }
    $$


---

### Fee

$L_{i,t} =$ liquidity in tick i at time t
$f_{i,t}$ = Fee of token Y collected in $L_{i,t}$

假设Alice在某tick范围内提供流动性S
则在t时刻，Alice获得的fee为：$f_t = S \sum_{i} \frac{f_{i,t}}{L_{i,t}}$
则从$t_0$到$t_N$时刻，Alice获得的fee为：$f=  \sum_{t=t_0}^{t_N} f_t $

#### Fee growth
   $$
      f_g = \frac{f_0}{L_0} + \frac{f_1}{L_1} + \frac{f_2}{L_2} + \cdots + \frac{f_N}{L_N} = \sum_{i=0}^{N} \frac{f_i}{L_i}
   $$
 
#### Fee growth inside ticks $\in [i_{lower},i_{upper}]$
  $$ fee\_growth\_inside = f_g - f_a -f_b $$
  $f_b$: fee growth below tick$i_{upper}$
  $f_a$: fee growth above tick$i_{lower}$

#### Fee growth below/avove
  1. 当 $i_{c} < i$时 
    $\underbrace{\overbrace{i_c,...,i-1,}^{f_b(i)}\overbrace{i,i+1,....}^{f_a(i)}}_{f_g}$
   $f_b(i) = f_g - f_o(i)$
   $f_a(i) = f_o(i)$

  2. 当 $i_{c} \geq i$时
       $\underbrace{\overbrace{...,i-1,i}^{f_b(i)}\overbrace{,i+1,....i_c}^{f_a(i)}}_{f_g}$
   $f_b(i) = f_o(i)$
   $f_a(i) = f_g-f_o(i)$
   所以有：
   $$
   f_a(i) =
   \begin{cases}
&f_g-f_o(i) & i_c \geq i\\
&f_o(i)  & i_c < i
\end{cases}
    $$
       $$
   f_b(i) =
   \begin{cases}
&f_o(i) & i_c \geq i\\
&f_g-f_o(i) & i_c < i
\end{cases}
    $$

#### Fee growth outside
   令 $f_o{i} = $ Fee growth outside at tick $i$
   Initialize:
          $$
   f_o(i) =
   \begin{cases}
&f_g & i_c \geq i\\
& 0 & i_c < i
\end{cases}
    $$
    Update:(when f_g crosses tick $i$)
    $$
    f_o(i) = f_g-f_o(i)
    $$

    