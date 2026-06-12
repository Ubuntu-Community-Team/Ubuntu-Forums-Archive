---
title: "starting whit scripting"
date: 2012-01-03
forum: General Help
---

### Post by hanskes on 2012-01-03
I want to make a script and have almost no experience with it..
I have a number of (.jpg) files in a directory and want to do a few commands with the first file in that directory. This is what I have:

R= ls -1 | head -1
echo $R

This is not working. When I try the first command i get as output the name of the file. When i try the second command I get:  ls -1 | head -1  and not the name of the first file.

Any help?:confused:

---

### Post by hanskes on 2012-01-03
i have found it..

R=$(ls -1 | head -1)

---

