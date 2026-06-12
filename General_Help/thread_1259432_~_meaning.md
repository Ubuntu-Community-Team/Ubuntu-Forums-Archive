---
title: "~ meaning"
date: 2009-09-06
forum: General Help
---

### Post by mentaaal on 2009-09-06
Hey guys, I am new to linux and am reading up on terminal usage. 
I have been puzzled by the meaning of the ~  character in scripts and in terminal usage in general. 

from what i have been told, when it is in the beginning of a file name, it is denoting a backup file. 

One example to illustrate my question is:
```
#!/bin/bash

count=0
for i in $(cat ~/.bash_profile); do
    count=$((count + 1))
    echo "Word $count ($i) contains $(echo -n $i | wc -c) characters"

```in this little script, i am not sure what the significance of the ~ is. 
Thanks for your help!

---

### Post by keplerspeed on 2009-09-06
~ is equivalent to /home/mentaaal/ your home directory.

---

### Post by Lucky75 on 2009-09-06
~ is your home folder for your user, sort of like my documents on windows. It's actual location is /home/username

---

### Post by mentaaal on 2009-09-06
Cool thanks for that!

---

### Post by 3rdalbum on 2009-09-06
I'm glad nobody told you to Google it:

> Your search - ~ - did not match any documents.

lol

---

### Post by mentaaal on 2009-09-06
> **3rdalbum said:**
> I'm glad nobody told you to Google it:



lol

Ha ha believe me i tried googling it but because it was only one character it was doubtful I would find anything useful!

---

### Post by Iowan on 2009-09-06
I've seen a couple of instances where the tilde (~) was used at the end of a filename for a backup file.

---

### Post by lovinglinux on 2009-09-06
You can also use $HOME on your scripts instead of ~.

---

### Post by Bachstelze on 2009-09-06
Just to make things clear: ~ is indeed a abbreviated form of your home directory, but this directory does not necessarily have to be /home/username.

---

### Post by fela on 2009-09-06
> **HymnToLife said:**
> Just to make things clear: ~ is indeed a abbreviated form of your home directory, but this directory does not necessarily have to be /home/username.

No, you can have your home directory on /jupiter if you want :D.

---

### Post by apmcd47 on 2009-09-06
> **Iowan said:**
> I've seen a couple of instances where the tilde (~) was used at the end of a filename for a backup file.

Yes, some editors will save the file as a backup with the name appended by a tilde. Emacs? Older users will remember Sun's OpenWindows texteditor had this behaviour.

It is also used by shells as a shortcut for another user's home directory: ~fred instead of /home/fred.

Andrew

---

### Post by oldos2er on 2009-09-06
> **Iowan said:**
> I've seen a couple of instances where the tilde (~) was used at the end of a filename for a backup file.

 Gedit does this by default.

---

### Post by orlox on 2009-09-06
Also, ~ not only can be used to refer to your home directory, but to any user directory. For instance, ~root refers to the home folder of the root user, and particularly, ~ by itself refers to the location of the current user home folder.

---

