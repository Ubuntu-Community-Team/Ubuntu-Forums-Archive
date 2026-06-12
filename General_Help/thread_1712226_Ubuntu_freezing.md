---
title: "Ubuntu freezing"
date: 2011-03-22
forum: General Help
---

### Post by lordjj on 2011-03-22
Hi, I've had Ubuntu for months but now it freezes at the login screen (Edit: I've written what I did when I last used Ubuntu in a post below.) 
Any suggestion on how to fix this? (like undo the xorg upgrades?)
Thanks.

---

### Post by deathadder on 2011-03-22
Can you switch to a virtual terminal (Ctrl+Alt+F1) and login from there? 

If so, are there any errors in:
/var/log/dmesg 
/var/log/Xorg.0.log

If you can't, is there an error displayed? Have you updated recently?

---

### Post by lordjj on 2011-03-23
Hi. I did 2 things that might have caused this last time I ran Ubuntu:

1- I added an xorg repository to my software sources and updgraded the intel graphics packages (I wanted to update the driver for my Integrated Mobile Intel 4 Series Express Chipset (rev07)
2- I added languages to the locale folder

When I boot normally, it freezes at the login screen. Nothing works, not even cntrl-alt-f1

If I boot in recovery mode and choose resume, I see:

```
cannot open locale definition file 'en_US.utf8': No such file or directory
```

If I boot in recovery mode and choose failsafeX, I get:
```
md5sum: etc/X11/xorg.conf: No such file directory
[...]
(EE) module ABI version (6) doesb't match the server's version (7)
(EE) Failed to load moduke "fdev" (module requirement mismatch, 0)
(EE) No drivers available

Fatal server error: no screens found

check "/var/log/Xorg.failsafe.log" for additional info
```

---

### Post by lordjj on 2011-03-25
I deleted the whole X11 folder and Reinstalled xserver-core, and Its back to normal! :grin:
 	Code:
 	rm -r /etc/X11
sudo apt-get remove xserver-core
sudo apt-get install xserver-core

---

