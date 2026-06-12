---
title: "problem with installing wubi"
date: 2011-03-13
forum: General Help
---

### Post by saeidj on 2011-03-13
Hello everybody
i have got a problem with wubi.
when i wanna install ubuntu via wubi at second step of installation it sticks and installation says remaining time 7h and sometimes 37h!!!!!!
and the installation never finish
I attached a picture 


many thanks

---

### Post by Triforcebrad on 2011-03-13
You can manually download the Ubuntu iso and if I remember correctly, you just put it in the Wubi folder and it should automatically detect it and use that iso, thus eliminating the need to download one on its own, which is where you problem is at. Hope this helps!:)

---

### Post by wilee-nilee on 2011-03-13
If it was me I would down load the ISO and burn it to a cd anyway and install from inside of windows then. The reason being is that the cd is your best friend as far as fixing problems.

So for example wubi uses the windows bootloader. But upgrades for Ubuntu's grub2 bootloader come through at times, and is known to put itself in the mbr replacing the MS bootloader leaving you with a un-bootable set up for anything on the HD. The cd will be used to fix this, and if you don't have one already then you will have to get one.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) 

So first watch the updates and upgrades once your installed and don't take any grub updates untick them in the update manager.

---

### Post by saeidj on 2011-03-13
thanks guys 
i downloaded the iso but i still have this problem :sad::sad:
nobody knows what is the exact problem?:sad:

---

