---
title: "sed finding item that contains double quotes"
date: 2011-07-28
forum: General Help
---

### Post by dentaro16 on 2011-07-28
hi,

i am trying to edit a huge configuration file for graphviz that contains IP addresses. unfortunately, some of the IP addresses didn't get parsed right and have only 3 octets. I am trying to use sed to find these 3 octet lines and delete the line entirely. example lines in the file look like this.

"22.210.73" -> "192.168.159";
"22.210.232" -> "22.210.248";

i have tried doing various things but to no avail. i had something that looked like this...

sed -i '/"*.*.*"/d' myfile

but i know that isn't correct....

help?

---

### Post by sisco311 on 2011-07-28
Try something like:
```
sed -r '/"([0-9]+\.*){3,3}"/d' file
```
-r = use extended regular expression in the script
[0-9]+ = matches a digit 1 or more times
\.* = matches a period 0 or more times 
(whatever){m,n} = matches the preceding element at least m and not more than n times
" = matches a "

EDIT: instead of \.* you could use \.{0,1} = match the period at least 0 but no more than 1 time.

---

### Post by dentaro16 on 2011-07-28
sisco311 you have saved the day.

thank you!

---

