---
title: "Symbolic Links with Absolute Paths?"
date: 2011-07-06
forum: General Help
---

### Post by Geremia on 2011-07-06
Is there a way to force [FONT=Courier New]ln[/FONT] to convert relative paths to absolute ones? [FONT=Courier New]man ln[/FONT] says:```
if later resolved, a relative link is interpreted in relation  to
       its parent directory.
```E.g., I want to avoid writing:```
ln -s "$(pwd)"/myfile /directory/of/mylink
```and just write:```
ln -s myfile /directory/of/mylink
```If I do not include the [FONT=Courier New]pwd[/FONT], resolving it later causes errors. [FONT=Courier New]ls -l[/FONT] would say "[FONT=Courier New]mylink -> [/FONT][FONT=Courier New]/another/directory/with/[/FONT][FONT=Courier New]myfile[/FONT]" instead of "[FONT=Courier New]/directory/of/mylink -> /another/directory/with/myfile[/FONT]". Why is this? Thanks

Let me do a specific example in case what I wrote above was unclear.```
$ ln -s DSC_7071.JPG ~/Desktop/test.jpg
cd ~/Desktop/
$ ls -l
lrwxrwxrwx 1 alan alan 12 2011-07-06 14:52 test.jpg -> DSC_7071.JPG
```Why doesn't it say the following?```
lrwxrwxrwx 1 alan alan 12 2011-07-06 14:52 test.jpg -> /directory/in/which/I/ran/ln-s/DSC_7071.JPG
```, where "/directory/in/which/I/ran/ln-s/" is where I ran [FONT=Courier New]ln -s[/FONT]? Thanks

---

