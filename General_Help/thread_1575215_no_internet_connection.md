---
title: "no internet connection"
date: 2010-09-15
forum: General Help
---

### Post by taylorp313 on 2010-09-15
im brand new to ubuntu. just got it successfully installed, but i can't get online. any thoughts?

---

### Post by cgb on 2010-09-15
How are you trying to connect?  Wireless or wired and is it through a Router or directly to the Modem?

---

### Post by taylorp313 on 2010-09-15
wireless.  through a router.

---

### Post by cgb on 2010-09-15
Does the wireless connection show up in Ubuntu but does not connect?  Does it appear to connect but still no internet access?  Or are you not seeing a wireless adapter period in your system tray?

---

### Post by taylorp313 on 2010-09-15
It shows up but doesn't connect.

---

### Post by cgb on 2010-09-15
you might need a different driver but not really sure yet..  So if you try to connect to your wireless network does it give an error message or what exactly happens?  Also what wireless card do you have?

---

### Post by Iowan on 2010-09-15
From a terminal (Applications>Accessories>Terminal), **sudo lshw -C network** You can redirect the output to a file via: **sudo lshw -C network > lshw.txt** which you can transfer to media (floppy, USB, CD, etc) so you can post it here.

---

