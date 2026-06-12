---
title: "Need help with Sed..."
date: 2012-05-09
forum: General Help
---

### Post by Alphamonkey on 2012-05-09
ok I am doing a lab for school and the teacher wants us to use sed. I have no idea how to perform the action with sed. I can do it with awk using

awk ' $4 > 99 {print}' file

What I need to know is how do I get sed to have a similar output which is: where it checks field 4 to see if the value is greater than 99 and then print it. I tried:

sed -n '/1[0-9][0-9]/p' file

but I do not know who to apply the /"filter"/ to a certain field to determine which lines to print. Somebody please help. Thanks.

---

### Post by papibe on 2012-05-09
Hi Alphamonkey.

Could you give us more information about the format of the input file?

Regards.

---

### Post by Alphamonkey on 2012-05-09
yeah its a file called cars lol

plym       fury              1970    73    2500
chevy     malibu           1999    60    3000
ford        mustang        1965    45    10000
volvo      s80               1998    102    9850
ford        thundbd         2003    15    10500
chevy      malibu          2000    50    3500
bmw       325i              1985    115    450
honda     accord          2001    30    6000
ford        taurus           2004    10    17000
toyota     rav4             2002    180    750
chevy      impala         1985    85    1550
ford        explor          2003    25    9500

my goal is to print only lines where field four is 100 or higher.

---

### Post by mörgæs on 2012-05-09
We don't support school work. Thread closed.

---

