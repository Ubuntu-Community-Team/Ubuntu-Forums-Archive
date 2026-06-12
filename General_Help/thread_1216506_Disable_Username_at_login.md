---
title: "Disable Username at login"
date: 2009-07-18
forum: General Help
---

### Post by ELF_O8 on 2009-07-18
Sup guys, Ubuntu forums has always been good to me, don't fail me now.

I'm in the process of creating a custom logon screen and would like to know if there was anyway to configure it and/or Ubuntu to just present me with a password box, i.e. I don't have to type in a username (I'm the only one on this computer).

Any way to do this?

---

### Post by wojox on 2009-07-18
I believe System > Admin > Login Window

Check Security tab enable automatic login.
But it won't prompt for password or username.

---

### Post by ELF_O8 on 2009-07-18
Thanks, but I was looking for a way of still having a password, but no username entry, like the username is implied.

---

### Post by HotForLinux on 2009-07-18
Edit :

/etc/issue
and
/etc/motd       (maybe a link but it doesn't matter)

for text before and after login
As far as I remember one of them was continuously modified according to a configuration somewhere.

---

### Post by HotForLinux on 2009-07-18
Sorry, if you want only the passwd prompt, .hmmm.....sounds like an agetty thing.
I don't think it's possible without modifying the agetty program. Let's see what other people say

---

### Post by ELF_O8 on 2009-07-18
Well, if that's the case, how would one go about modifying the agetty program.

---

### Post by HotForLinux on 2009-07-18
You have to download the source of the getty program you see when you list
> **user@mon-pc****:~$ ****ps au**How?
> **usuari@my-pc~$ which getty**
/sbin/getty

**usuari@tolva-min:~$ whereis getty**
getty: /sbin/getty /usr/share/man/man8/getty.8.gz

**usuari@mon-pc:~$ dpkg -S /sbin/getty**
util-linux: /sbin/gettyTherefore, the command to download the sources for that package is:
> **usuari@mon-pc:~$ sudo apt-get source util-linux** But I'm _not sure_ that's the correct and the only solution, you should ask more

More info:
> **usuari@mon-pc:~$ man  apt-get**
**usuari@mon-pc:~$ man  dpkg**

---

