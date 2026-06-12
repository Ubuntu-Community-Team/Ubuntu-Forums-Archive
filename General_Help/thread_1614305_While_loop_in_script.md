---
title: "While loop in script"
date: 2010-11-05
forum: General Help
---

### Post by calvarymanagua on 2010-11-05
I am trying to create a while loop in a shell script.  I am just learning this and looked at a few examples.  I wrote this script:

#!/bin/bash


COUNT=6

 while [ $COUNT -le 0]; do
   echo Value of count is: $COUNT
   let "COUNT=COUNT-1"
 done

However, I am getting the error:
line 6: [: missing `]'

---

### Post by CharlesA on 2010-11-05
Add a space between the 0 and the ]

---

