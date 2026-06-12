---
title: "check a directory for unique files"
date: 2012-01-05
forum: General Help
---

### Post by coffeecake on 2012-01-05
hi. I have a directory containing lots of files and i want to make sure that they are all unique. I thought of performing a hash check and checking for any duplicates. But how can i do that in a bash script using one for loop since there is no way to store arrays ? Since there is no way to store stuff i will have to make use of two for loops. But is there a much easier method ? or maybe a tool to do this for me ?

---

### Post by papibe on 2012-01-06
You can do it in stages using files. For example:
- You can get all the sums into a file.
- Then, check the file for duplicates.

Tell us if you need more directions.
Regards.

---

### Post by sisco311 on 2012-01-06
You can use arrays in bash:  [http://mywiki.wooledge.org/BashGuide/Arrays](http://mywiki.wooledge.org/BashGuide/Arrays)

But you could simply use fdupes. It's in the repositories.

---

