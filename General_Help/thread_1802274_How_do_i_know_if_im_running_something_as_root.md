---
title: "How do i know if im running something as root?"
date: 2011-07-11
forum: General Help
---

### Post by GlacialFlames on 2011-07-11
Hi! I'm very new to Linux, i'm running Ubuntu and i'm trying to install a program. In the instructions it says
"Check that you ARE NOT root, never run similar tools as root! just change file permissions"

How do i check if i'm root or what am I supposed to do here? Thanks!

---

### Post by thefasterblueone on 2011-07-11
> How do i check if i'm root or what am I supposed to do here? Thanks!

```
whoami
```

---

### Post by Frogs Hair on 2011-07-11
If you have created and logged into  a user account with limited permissions you are not running as root . Also if you have not started the program in the terminal using the sudo command  you are not running as root. 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by GlacialFlames on 2011-07-11
Thank you both for replies!

So as long as i don't use the sudo command i'm all good ?

---

### Post by pqwoerituytrueiwoq on 2011-07-11
or gksu/gksudo

---

### Post by WorMzy on 2011-07-11
If something asks you for your password when you try to open it, then it will open as root.

---

### Post by hawthornso23 on 2011-07-11
The program you are trying to install - make sure it isn't in the repositary first. In ubuntu you should only rarely need to install something downloaded from a website. Most everything you need is already in the repositaries and can be installed with a single click.

---

### Post by nothingspecial on 2011-07-12
By default (unless you've messed with your prompts, which I'm guessing you haven't), if your prompt (the bit before the blinking cursor) ends with a $, then you are a user.

If it ends with a # then you are root.

---

