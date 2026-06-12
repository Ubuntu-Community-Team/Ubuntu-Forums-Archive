---
title: "Bash Script Help"
date: 2009-11-25
forum: General Help
---

### Post by Crazyx on 2009-11-25
Hey there,
I just started learing ubuntu and my teacher got me to do a calculator on the bash script using the editor. I did the +,-,* and / operations but i don't know how to determinate a sin,cos,tan,cotan,logarithm and exponential of a number. I searched everywhere and find nothing...
Here is my work so far:

#!/bin/bash
echo " (1- addiction; 2- subtraction; 3-; 4-division; 5-Sin; 6-Cos; 7-Tan; 8-Cotan; 9-logarithm; 10-exponential)"
read STR
case $STR in
1)
echo "write a number"
read STR1
echo "write another"
read STR2
echo $STR1 + $STR2 "=" $[$STR1 + $STR2];;
2)
echo "write a number"
read STR1
echo "another"
read STR2
echo $STR1 - $STR2 "=" $[$STR1 - $STR2];;
3)
echo "first number"
read STR1
echo "second"
read STR2
echo $STR1 x $STR2 "=" $[$STR1 * $STR2];;
4)
echo "first number"
read STR1
echo "second"
read STR2
echo $STR1 / $STR2 "=" $[$STR1 / $STR2];;
esac


If you could tell me how can i do the rest ill be very gratefull...

---

### Post by ghostdog74 on 2009-11-25
use awk

just one example for you
```

$ awk 'BEGIN{print sin(90) }'


```

---

### Post by Elfy on 2009-11-25
Closed - homework is for you not us.

---

