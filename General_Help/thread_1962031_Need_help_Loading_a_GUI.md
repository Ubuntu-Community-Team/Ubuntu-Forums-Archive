---
title: "Need help Loading a GUI"
date: 2012-04-20
forum: General Help
---

### Post by Zemallo on 2012-04-20
Ok so im new to linux and i am unfomiliar with the commands in the terminal. I used unetbootin to load a bootable flashdrive with Ubuntu 10.04_Live when i boot from the usb i get stopped by a terminal and im unsure of the command to take me to the desktop gui

---

### Post by coldraven on 2012-04-20
It should boot straight into the desktop so I suspect that either your Live .iso file or the USB  is corrupt.
Need more info..
Did you burn the .iso to a CD or create the USB drive directly from the file?
How far does the boot-up process get and what messages do you see?

You can check the MD5sum of the downloaded file or CD from the info here.
[http://releases.ubuntu.com/10.04.4/](http://releases.ubuntu.com/10.04.4/)

[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by alphaamanitin on 2012-04-20
Many Radeon HD 6XXX graphic cards fail to load properly (bad drivers or something in kernal) and cause live installations to fall to terminal, and actual installs as well.  I have had this problem on Fedora, live Kubunut, Ubuntu Xbuntu, and others.  Havn't figured out how to fix it yet.

AlphaA

---

### Post by bogan on 2012-04-20
Hi!, **zemallo**,

In the terminal run: ```
sudo service gdm start
```That should get you a GUI screen if everything is OK, if not run 'sudo startx' and note any error messages.


Post:>  lspci -nnk | grep VGA

Chao!, **bogan**.

---

