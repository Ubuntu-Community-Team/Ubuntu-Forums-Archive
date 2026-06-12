---
title: "No login window shows up after boot"
date: 2010-09-14
forum: General Help
---

### Post by tonyatvt on 2010-09-14
Everything looks fine until when the login screen should show up but doesn't. The cursor is there and can move.
 I can switch to terminal by *ctl-alt-F**, and login. After *gdm stop* and *startx*,  gnome is back but only in fail safe mode, with non-movable  non-resizable window, only one workspace, and cursor is a black cross...

I ever met a similar case before, which comes to the login screen but it  keeps reloading after entering password. Finally got solved by run *sudo apt-get install --reinstall ubuntu-desktop* in terminal. This time it doesn't work anymore.

Please help, I really can't bear reinstall the system because I configured many programs. Thank you!

---

### Post by musdem on 2010-09-14
why not try reinstalling gnome from the terminal 
sudo apt-get install ubuntu-desktop
OR
sudo apt-get install gnome

---

### Post by tonyatvt on 2010-09-15
Thank you. I tried sudo apt-get install ubuntu-desktop, but it doesn't work (although it works last time when repeating login happened).

I will try install gnome tomorrow. Reinstall gnome will not affect other programs in the system?

> **musdem said:**
> why not try reinstalling gnome from the terminal 
sudo apt-get install ubuntu-desktop
OR
sudo apt-get install gnome

---

### Post by FahadMKS on 2010-09-15
You might have enabled the option of Auto Login.
You will have to turn it off.

I will help you.

 The auto login feature is on GDM, so you have to edit the config file.

> sudo gedit /etc/gdm/gdm.conf
Look for AutomaticLoginEnable and set it to false...

This should do the trick

---

### Post by tonyatvt on 2010-09-15
Thank you. I can't find gdm.conf in the directory you pointed out. There is a gdm.conf in /etc/init/gdm.conf, but it doesn't contain the option. 

I think the key information is if I login in terminal, and startx, it always start the fail safe mode.

> **FahadMKS said:**
> You might have enabled the option of Auto Login.
You will have to turn it off.

I will help you.

 The auto login feature is on GDM, so you have to edit the config file.

sudo gedit /etc/gdm/gdm.conf
Look for AutomaticLoginEnable and set it to false...

This should do the trick

---

### Post by tonyatvt on 2010-09-15
Now I have some progress. Inspired by this post

[http://osdir.com/ml/ubuntu-users/2010-07/msg01578.html](http://osdir.com/ml/ubuntu-users/2010-07/msg01578.html)

I realize I also installed zlib before crash, so I uninstalled it. Now the login screen shows up, but after login it still fail safe mode, only the cursor back to normal. Still one workspace, non-movable window.

---

### Post by musdem on 2010-09-15
No it shouldn't affect any programs except the ones that come in the gnome packages (e.g. Nautilus) Also you may want to find more programs that you recently installed other than zlib. I hope this helps :)

---

