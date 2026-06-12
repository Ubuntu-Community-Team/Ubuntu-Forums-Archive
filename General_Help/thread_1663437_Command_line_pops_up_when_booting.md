---
title: "Command line pops up when booting"
date: 2011-01-09
forum: General Help
---

### Post by Xoniac on 2011-01-09
Alright guys, I just installed Ubuntu (10.10) via USB. Installation went perfectly, and then I installed videocard drivers. I restarded and from then when I boot, some kind of command line pops up and wants me to login from there. I did, and ive also looked at this thread: [http://ubuntuforums.org/showthread.php?t=978882](http://ubuntuforums.org/showthread.php?t=978882) and tried to restart GNOME but didnt work :(

What to do?

Note: I'm new to Linux

---

### Post by TeoBigusGeekus on 2011-01-09
What is your graphics card?
If you don't know, run
```
lspci | grep VGA
```
to find out.

---

### Post by Xoniac on 2011-01-10
> **TeoBigusGeekus said:**
> What is your graphics card?
If you don't know, run
```
lspci | grep VGA
```
to find out.

I just tried it but it doesnt show anything. Although my Laptop is a Acer Aspire 3820 (core i3, 13,3")

---

### Post by Xoniac on 2011-01-12
Bump this up. Still havent been fixed. :(

---

### Post by Xoniac on 2011-01-13
Still hasnt been fixed.. A friend of mine told me that I should try install an xfce version, is ubuntu already that or where will I find a xfce version?
 
- Thanks in advance

---

### Post by celldweller1591 on 2011-01-13
if you installed Ubuntu 10.10 basic, lke from Ubuntu.com directly, then its Gnome. If you installed Xubuntu, then its Xfce. There is no need to change your Desktop environment. 
Tell me what error message is shown when you login from the command line and type :- 
> startx 
or
> sudo /etc/init.d/gdm start
For the time being, try to boot ubuntu into safe graphics mode from Grub options at boot time. (IInd option generally). See if its working.

---

### Post by Xoniac on 2011-01-14
I really appriciate you wanting to help me, but I tried install xubuntu, and everything's fine now.

Thanks for the help everyone.

Although I do wonder how my laptop cannot run ubuntu 10.10 (laptop version) when my laptop is only 4 months old :o

---

