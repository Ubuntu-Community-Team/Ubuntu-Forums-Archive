---
title: "Help: apply script to all directory"
date: 2011-02-18
forum: General Help
---

### Post by WDYSUN on 2011-02-18
Dear Forumers

I have the following  script which takes all jpeg immages in a directory and rename the files according to EFIX data.

this is my RENJPG script which is executable for all users:

```

#!/bin/bash

for i in *.[jJ][pP][gG] *.[jJ][pP][eE][gG];
do
   jhead -autorot -nf%Y-%m-%d_%H.%M.%S "$i"
done

```


Now I have my /home/user/images directory where I store all my collection of pictures, this is organised with a number of subdirectory.

I would like to have a script that apply RENJPG to all directories in /home/user/images.

I tried something but I couldn't succeed! Any help?

Best Regards
Pietro

---

### Post by sisco311 on 2011-02-18
You don't need the for loop.

Assuming that you have bash4, you could do:
```
shopt -s globstar failglob
cd /home/user/images 
jhead -autorot -nf%Y-%m-%d_%H.%M.%S **/*.[jJ][pP][gG] **/*.[jJ][pP][eE][gG]
```
or
```
shopt -s globstar failglob
jhead -autorot -nf%Y-%m-%d_%H.%M.%S ~user/images/**/*.[jJ][pP]{[eE],}[gG]
```

---

### Post by DaithiF on 2011-02-18
you can also simplify things a little by using nocaseglob

```
shopt -s nocaseglob
```

then 
**/*.jp{e,}g

will match JPG, jpg, JPEG, jpeg, etc.

---

### Post by WDYSUN on 2011-02-18
I tried both on a test folder and it doesn't work, it says 


```

bash: no match: **/*.[jJ][pP][eE][gG]

```

Best
Pietro

---

### Post by sisco311 on 2011-02-18
Oops, my bad.   :)

Either use two jhead commands:
```
shopt -s globstar failglob nocaseglob
cd /home/user/images 
jhead -autorot -nf%Y-%m-%d_%H.%M.%S **/*.jpg
jhead -autorot -nf%Y-%m-%d_%H.%M.%S **/*.jpeg

```

or nullglob instead of failglob; and let the command to fail if there are no .jpg or .jpeg files in the directory or in its subdirectories:
```

shopt -s globstar nullglob nocaseglob
cd /home/user/images 
jhead -autorot -nf%Y-%m-%d_%H.%M.%S **/*.jp{e,}g || echo error
```

---

### Post by WDYSUN on 2011-02-18
Great! Solved!

Thanks a lot
Pietro

---

