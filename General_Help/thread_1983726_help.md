---
title: "help"
date: 2012-05-20
forum: General Help
---

### Post by wis5.2 on 2012-05-20
can not intsal ubuntu on a windows 98 and xp server need step bye step [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Cheesemill on 2012-05-20
How are you trying to install Ubuntu, what steps have you taken?
What happens when the installation fails, do you get any error messages?

For installation instructions see here:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Old_Grey_Wolf on 2012-05-20
What is the CPU and memory specs of the computer? If it is running Windows 98 or XP, it may not be enough for Ubuntu. You may need something lighter.

---

### Post by wis5.2 on 2012-05-21
tried to format the hard drive but the drive seem lock so i boot by using f6 and booted by cd first and i install ubuntu 9.04 . now trying to install the lattes firefox but as normal i mixe avery thing up. I downlaod the lattes firefox and i extacted it to the desktop now icon firefox-12.0.tar.bz2 and firefox folder is on desktop i want to get rid of it and a open the application with a bleu icon (application/x-execuable)what do i do ? .

---

### Post by zombifier25 on 2012-05-21
1. 9.04 is no longer supported. Where did you get the CD?

2. When you download Firefox directly from their website, you get a tarball that contains a functional, portable Firefox itself, no need to install.

---

### Post by wis5.2 on 2012-05-21
cd comes from distro and firefox got directly from firefox website but i must a extracted in the wrong place ,i put download and extract file on desktop can i erase it and start over again ? machine is a p4 2.9 with 256 meg just look at Installing Ubuntu with the Windows installer and can i try it an a windows 98 with p3 and 126 meg and the p4 with ubuntu 9.04 .

---

### Post by Old_Grey_Wolf on 2012-05-22
Ubuntu 9.04 is no longer supported. You will not be able to get updates for it. The repositories for software have been moved to old-releases.

Ubuntu 9.04 Desktop version had the following recommended system hardware specs:

700 MHz x86 processor
384 MB of system memory (RAM)
8 GB of disk space

You need to download something newer (10.04, 11.04, 11.10, or 12.04) and lighter Desktop like Lubunu (LXDE) or Xubuntu (XFCE).

I'm curious about you having installed Ubuntu 9.04 on your computer. Please enter the following commands in a terminal and post the output in this thread (It is a small letter L not a number 1 in the commands).

This command tells me where Ubuntu is installed.```
df -h
```
This command tells me what version is installed.```
cat /etc/lsb-release
```

This command tells me what Desktop you are using.```
dpkg -l | grep ubuntu-desktop
```

---

### Post by wis5.2 on 2012-05-25
where do i type in this command ?

---

