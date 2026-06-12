---
title: "Tar gives &quot;gzip: short wrtie&quot;"
date: 2011-07-24
forum: General Help
---

### Post by abhishekdey1985 on 2011-07-24
Hi,

I have an application that extracts certain BLOB data from data base and copies them to /tmp/ folder. I then use "cd /tmp/ && tar -czvf <Package Name> <Folder Name>" to create tar files, which is called in System() function.

The problem is it says 

gzip: short write
and creates an empty package which is not desired. but when i enter the same through terminal, it creates it with no problem.

please help me rectify this problem.

regards.

---

