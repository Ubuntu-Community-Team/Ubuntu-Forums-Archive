---
title: "BASH Scripting"
date: 2010-08-05
forum: General Help
---

### Post by aidenscool09 on 2010-08-05
Will it be possible to make a bash script that will read what the user is typing and output to a file (not a keylogger). So, for example, when you try to install something, it doesn't show anything while you type your password. is it possible to do that sort of thing in a bash script. So you type a section invisibly and then it saves whatever you typed to a text file. Here's an example of what I mean:
```

#!/bin/sh

user="/home/$USER/newuser"

echo Make a Username
read user
grep "user" "newuser"
echo make a password password for $(echo $USER):
read paswd
grep "pswd" "pswd"

```
i don't think i've done it right but can anybody hep with this?

---

### Post by sisco311 on 2010-08-05
```

stty -echo
read passwd
stty echo

```

---

### Post by nothingspecial on 2010-08-05
> **sisco311 said:**
> 
stty -echo

Turns your keyboard input off in the console
> **sisco311 said:**
> 
stty echo

  Turns it on again

---

### Post by aidenscool09 on 2010-08-05
thanks. And also, i'm working on another script now, i'm making a bash compiler, so could you be any kinder and give some help with that, too? Thanks so much in advance.

---

