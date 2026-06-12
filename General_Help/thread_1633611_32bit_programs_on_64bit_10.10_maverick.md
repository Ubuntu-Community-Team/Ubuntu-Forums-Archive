---
title: "32bit programs on 64bit 10.10 maverick"
date: 2010-11-29
forum: General Help
---

### Post by ahmed shabayek on 2010-11-29
need help guys i need help setting up chroot for my system so i can use 32bit programs, i have gone through the steps same as the old versions but it doesnt seem to work can any body go with me through the steps again or suggest a way to work 32bit programs on the 64bit platform

---

### Post by philinux on 2010-11-29
> **ahmed shabayek said:**
> need help guys i need help setting up chroot for my system so i can use 32bit programs, i have gone through the steps same as the old versions but it doesnt seem to work can any body go with me through the steps again or suggest a way to work 32bit programs on the 64bit platform

Which apps?

---

### Post by ahmed shabayek on 2010-11-29
so far its only the pcsx2 0.9.7  thts bothering me

---

### Post by Billt Joe on 2010-11-29
All I had to do was install "liba-32" from synaptic to get 32bit apps working. I can't remember if that's the exact name but it is worth a try.

---

### Post by oldos2er on 2010-11-29
It's ia32-libs

---

### Post by Billt Joe on 2010-11-29
I was close :D

---

### Post by ahmed shabayek on 2010-11-29
thnx guys ill it hope it works:D

---

### Post by ahmed shabayek on 2010-11-30
i installed it but i cant seem to get the pcsx2 working thnx anyway

---

### Post by ahmed shabayek on 2010-12-02
so that trick didnt work i always get the message libwx_baseu-2.8.so.0: cannot open shared object file: No such file or directory     can any body help me configure and use chroot

---

### Post by oldos2er on 2010-12-02
Looks like it needs libwxbase2.8-0

---

### Post by ahmed shabayek on 2010-12-02
yes but i already installed it from ubuntu software center before i started so how come it produces this error

---

### Post by oldos2er on 2010-12-02
Did you follow [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian) ?

---

### Post by mc4man on 2010-12-02
It's possible that you may need to install the 32 bit lib in question. (wouldn't exactly know without trying.

If so the using getlibs makes it quite simple
(getlibs -p <package name>
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by ahmed shabayek on 2010-12-03
thnx guys for ur help i managed to fix it using this post [http://ubuntuforums.org/showthread.php?p=10193760#post10193760](http://ubuntuforums.org/showthread.php?p=10193760#post10193760) , the answer turned out to be a very simple one sorry for all your trouble and thnx again

---

