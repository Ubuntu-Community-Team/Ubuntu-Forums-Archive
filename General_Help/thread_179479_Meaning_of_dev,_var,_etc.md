---
title: "Meaning of /dev/, /var/, etc"
date: 2006-05-20
forum: General Help
---

### Post by Mau on 2006-05-20
Can anyone explain to me th meaning behind /dev/, /var/, /bin/, /etc/, /use/, /opt/, etc?  So far everything seems random as to what goes where, but there must be a system.  :KS

---

### Post by user1397 on 2006-05-20
[quote=Mau]Can anyone explain to me th meaning behind /dev/, /var/, /bin/, /etc/, /use/, /opt/, etc?  So far everything seems random as to what goes where, but there must be a system.  :KS[/quote] i'm not sure about /var or /etc, but i can at least say from what ive seen and heard that /bin is reserved for program commands (starting a program), /opt is a root directory where you might want to save some of your downloaded program folders, /dev maybe stands for development? i dont really know that one..., /usr is where all of your applications' data, icons, and shared documents between all users are...srry for the unclear info, im just saying what i think!

i might be wrong on some of these, so don't take my info as completely correct!

---

### Post by jazzmuzik on 2006-05-20
I've always wondered about this myself. I don't know all the answers, but here's a start:

/dev - links to DEVices like hard drives, floppy drives, sound devices, etc.

/var - log files, caches and spools

/bin - 'BINaries'; a binary is an executable program, the equivalent of an exe file in DOS/Windows. Most user binaries are in /bin or /usr/bin and system binaries for maintaining the system used by the sysop are in /usr/sbin/ or /sbin/

/etc - configuration files for the system; mostly text based config files

---

### Post by Jucato on 2006-05-20
Here's a link to help you out:
[https://wiki.ubuntu.com/LinuxFilesystemTreeOverview?highlight=%28filesystem%29](https://wiki.ubuntu.com/LinuxFilesystemTreeOverview?highlight=%28filesystem%29)
It's just basic, so don't expect any in-depth explanation.

Btw, /dev is for devices, /bin, which is located under /usr (so it's really /usr/bin) is for binary files (a.k.a. executable files, the Linux counterpart of MS .exe), /etc is where configurations are stored, /media (or /mnt in some distros) cotain mount points for devices (in /dev). Just check out that link I gave for some brief explanations. 

Hope that helps.

EDIT: more in-depth explanations (just for future reference)
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Mau on 2006-05-20
Great, thanks for the replies!

---

