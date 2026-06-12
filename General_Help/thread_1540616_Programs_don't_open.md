---
title: "Programs don't open"
date: 2010-07-28
forum: General Help
---

### Post by mailbk247 on 2010-07-28
Hello, am an Ubuntu newbie.
After installing ubuntu, I tried accessing the menu edit option and the program doesn't open. It doesn't even bring up the loading symbol. I installed picasa (photo editor) and it behaved similarly like the menu edit. Is there a fix, or am i missing something.
thanks

---

### Post by ronnielsen1 on 2010-07-28
Type picasa from a terminal and see if it opens

---

### Post by mailbk247 on 2010-07-28
i tried that and it gave me the following error

/usr/bin/picasa: line 139:  1962 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  2065 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

i don't think the main menu should have the same problem

---

### Post by ronnielsen1 on 2010-07-29
Where did you get the cd you installed ubuntu from. If you burned this yourself it might be a bad burn. Is this a normal installation or wubi? Also where did you get the picasa download? I assume you did get the deb and not the exe.

Also from root (see if it works) try sudo picasa. I've googled up references to people being able to run as root instead of user. If it works, we're getting closer to figuring out the problem

---

### Post by mailbk247 on 2010-07-29
okay, thanks for the reply
i'm using the normal install not wubi
i got the deb instead of the and exe, I think exe's don't work on ubuntu unless you are using wine
i think the using root would solve the problem, but how do i login to my computer as root not user.
thanks

---

### Post by dino99 on 2010-07-29
follow this link:

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

---

