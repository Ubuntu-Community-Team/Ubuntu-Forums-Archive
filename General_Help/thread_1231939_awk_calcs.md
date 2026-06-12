---
title: "awk calcs"
date: 2009-08-05
forum: General Help
---

### Post by ub007 on 2009-08-05
I've got this file a1.txt which reads

1000 2000 3000 4000

I wish to divide alll the values by '.004096' & get them to excel format as well.

tried

> cat a1.txt | awk '{print $1*.004096 "\t" $2*.004096 "\t" $3*.004096 "\t" $4*.004096 }' > excelformat.txt
Now I get 

> 40.96   8.192   12.288   16.383

How do i format it to the nearest decimal place as in

> 41 8  12  16


David

---

### Post by Glyndwr on 2009-08-05
You can use printf instead of print to get a decimal place format.

Have a go with something like:

cat a1.txt | awk '{printf "%d %d %d %d\n", $1*.00496, $2*.00496, $3*.00496, $4*.00496}'

---

### Post by llamabr on 2009-08-05
I would think you could just open this right with oocalc, and do the math you want in there.  oocalc will recognize tab or space as a field delimiter.

---

### Post by kjohri on 2009-08-05
You can add 0.5 to each expression to get better rounding. That is,

$ cat a1.txt | awk '{printf "%d\t%d\t%d\t%d\n", $1*.004096 + 0.5, $2*.004096 + 0.5, $3*.004096 + 0.5,  $4*.004096 + 0.5 }'

---

