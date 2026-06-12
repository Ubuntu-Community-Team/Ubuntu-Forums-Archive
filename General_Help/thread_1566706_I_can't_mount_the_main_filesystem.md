---
title: "I can't mount the main filesystem"
date: 2010-09-02
forum: General Help
---

### Post by elmasry.ayman on 2010-09-02
I have ubuntu and windows installed on my computer, and sometimes I would need something from the folders I have on windows and I would mount the main hard drive. But now it's telling me "Not Authorized"

What's up with that?

---

### Post by darolu on 2010-09-02
You need to mount it with root privileges; open a terminal and run:
```
sudo fdisk -l
```
That's a lowercase "L" btw; it will print a list with your filesystems, identify your Windows one and use the information to run:
```
sudo mount [color="darkred"]/dev/sda1[/color] -o defaults /mnt/
```
This will mount your filesystem to /mnt directory and will let you use it normally; if you don't want to do this every time you want to access it, edit your [fstab]("https://help.ubuntu.com/community/Fstab") file so it gets auto-mounted when you log in.

More info about it at:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

