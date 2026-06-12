---
title: "Dell Inspiron E1505"
date: 2006-05-02
forum: General Help
---

### Post by RoninGurl on 2006-05-02
I can't boot the Ubuntu LiveCD with my Dell Inspiron E1505. It has the ATI Mobility Radeon X1300, standard built-in soundcard in E1505, 1GB of RAM, T2500 Dual Core processor and the 15.5" WSXGA LCD screen. Everytime I try to load the LiveCD, Dapper Drake Beta 2 or Breezy Badger 5.10, it says that the xwindows thing is not configured right. I dont know how to copy and paste the entire error and save it to a file on the C:\ drive or I would have. But it refuses to boot on the E1505 Inspiron by Dell.

Any help?

---

### Post by RoninGurl on 2006-05-02
Anyone?

Oh. *smacks self* Umm, can someone put this in laptops forum?

---

### Post by syadnom on 2006-05-06
[QUOTE=RoninGurl]Anyone?

Oh. *smacks self* Umm, can someone put this in laptops forum?[/QUOTE]
you need to got to a console (Ctrl+F4) and edit the /etc/X11/xorg.conf, you can do this with nano or vi

sudo nano -w /etc/X11/xorg.conf 
OR
sudo vi /etc/X11/xorg.conf

then fir the "ati" line in the Device section(in nano Ctrl-W for search)

change that line from "ati" to "vesa"(with vi hit the 'i' key to go interactive)

then save
with nano Ctrl-X and choose yes
with vi hit escape, then type :wq (thats : = prompt,w=write,q=quit)

now at the prompt type 
sudo /etc/init.d/gdm restart (or kdm in kubuntu!)

now you will be able to start up X in vesa mode and run the installer.

after install just use forums and do the fglrx driver for accellerated video.  i dont think the open source ati driver( the "ati" from above) works with a radeon x1300 or x1400.

good luck.  works fine on my e1505, the newest fglrx driver work well also.

e1505
1.66 core duo
1GB Ram
X1400

---

