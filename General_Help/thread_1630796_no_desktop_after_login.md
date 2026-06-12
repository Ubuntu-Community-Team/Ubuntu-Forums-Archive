---
title: "no desktop after login"
date: 2010-11-25
forum: General Help
---

### Post by qweru on 2010-11-25
Hi all
I have a very big problem.
After booting into ubuntu 10.04 i saw only my wallpaper and the still moving mouse courser but nothing elese.

No desktop no panel nothing.

i pressed alt+print+k to go back to login screen and i logged in with xterm session but every app i started either didn't show up or freezes immediately.

can someone help me please troubleshoot this without to reinstall the hole system?

---

### Post by qweru on 2010-11-26
Is there a way to see why this is happening?

This never happened with hardy i was 2 years long a happy ubuntu user and now this :(

---

### Post by sikander3786 on 2010-11-26
First of all, I would recommend to re-install the ubuntu-desktop package.

Press Ctrl + Alt + F1 at your login screen. Login to the console using your credentials and do this command.

```
sudo apt-get install --reinstall ubuntu-desktop
```

If that returns some error,

```
sudo dpkg --configure -a
```

Press Ctrl + Alt + F7 and login to the desktop. Any difference now?

It would be helpful if you post the errors encountered there.

---

### Post by qweru on 2010-11-26
Hey thank you very much for your reply.
i ran the command from recovery root shell because on normal login all tty's have graphical glitches. so i ran the command and it reinstalled the ubuntu-desktop without errors so i restarted but i have still the same problem.
 it seems all launching apps becoming zombis after starting them. 

i also tried to look for /var/log/ for error messages from a live cd but it didn't exist
so i dont know how to give more information 

Please any help is appreciated

---

### Post by sikander3786 on 2010-11-27
> **qweru said:**
> Hey thank you very much for your reply.
i ran the command from recovery root shell because on normal login all tty's have graphical glitches. so i ran the command and it reinstalled the ubuntu-desktop without errors so i restarted but i have still the same problem.
 it seems all launching apps becoming zombis after starting them. 

i also tried to look for /var/log/ for error messages from a live cd but it didn't exist
so i dont know how to give more information 

Please any help is appreciated
Please post your hardware specs including Graphics Card and RAM.

And when did this problem arise? After some kind of updates.... Or just random?

---

### Post by qweru on 2010-11-27
My pc is a fujitsu Siemens desktop with amd athlon 64 x2 3800+ 1 gb ram and a radeon x1600

I dont really know what i did i just shut down my pc and on the other day it was like this

---

### Post by sikander3786 on 2010-11-28
Try these.

```
sudo dpkg --configure -a
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo dpkg-reconfigure -phigh -a
```

---

