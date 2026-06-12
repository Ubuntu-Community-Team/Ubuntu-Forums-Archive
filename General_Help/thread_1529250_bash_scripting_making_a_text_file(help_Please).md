---
title: "bash scripting: making a text file(help Please)"
date: 2010-07-12
forum: General Help
---

### Post by william_lane on 2010-07-12
Hi I am tying to write a script that asks for user input and saves it to a text file using awk
so example
#!/bin/bash
read a
awk #saves to file

I had a working scripted last night, deleted it by mistake and for the life of me can not remember how i did it. Thank you to anyone who may help...

---

### Post by chessnerd on 2010-07-12
You can just use this:

```
echo Data > Filename.txt
```
That will write Data to a new file called Filename.txt.

If you do this:
```
echo Data >> Filename.txt
```
It will append Data to the existing file Filename.txt.

---

### Post by william_lane on 2010-07-12
[chessnerd]("http://ubuntuforums.org/member.php?u=804379"): Thank you alot it is working now:popcorn:

---

