---
title: "netbook issue"
date: 2011-01-08
forum: General Help
---

### Post by pockets1 on 2011-01-08
I installed ubuntu "alongside" widows on my gateway netbook and I cannot get it to work or get back to windows.
Help!!

---

### Post by LetsMugSanta on 2011-01-08
What version of the Ubuntu netbook is it. How far did you get and what exactly happened and happens now when you boot it up.

---

### Post by Bucky Ball on 2011-01-08
Welcome.

Does it work with Ubuntu? As much info as you can about what happened, please, and what's happening when you boot. ;)

---

### Post by pockets1 on 2011-01-08
10.10 netbook i386 iso

---

### Post by LetsMugSanta on 2011-01-08
Mind providing any information as to what particularly happened as best as you can remember as to what you did? What also happens when currently booting up (exactly what happens in as much detail as possible).  You need to help us so we can help you.

---

### Post by pockets1 on 2011-01-08
it boots to ubunto but its messed up. "blank" icons pop up when i move the cursor over them. I can open up some things but the graphics are jacked up.

---

### Post by Bucky Ball on 2011-01-08
> **pockets1 said:**
> 10.10 netbook i386 iso

More please. EXACT description of problem if possible. ;)

---

### Post by pockets1 on 2011-01-08
I followed the instructions on how to get ubuntu for my netbook. these were the instructions on the ubuntu site. I downloaded the file and then created a usb drive. I installed it "alongside" windows.

---

### Post by LetsMugSanta on 2011-01-08
Model of netbook also?

---

### Post by pockets1 on 2011-01-08
gateway LT3103u

---

### Post by LetsMugSanta on 2011-01-08
Any more information on exactly what happened? Also when installing Ubuntu did you have any issues? Are you able to use the update manager or driver manager. These usually pop up when you first reboot after a few minutes.

---

### Post by pockets1 on 2011-01-08
The install seemed to go ok. i cannot get to the update manger or driver. on start up it goes to a screen where I select the OS. It lists ubuntu, ubuntu recovery,memory tests,vista, and windows recovery.
If I select ubunto it goes to the desk top but its messed up. if i go to windows vista it asks if i want to reinstall windows.

---

### Post by Bucky Ball on 2011-01-08
Boot ubuntu from the medium you installed it with (probably a usb dongle). Once you're at the desktop, find Gparted Partition Editor and look for an NTFS partition. If there isn't one, Windows has been wiped. Do this and get back to us. ;)

---

### Post by LetsMugSanta on 2011-01-08
Alright, during the installation how did you set the partitions from the Ubuntu setup.

---

### Post by Bucky Ball on 2011-01-08
> **LetsMugSanta said:**
> Alright, during the installation how did you set the partitions from the Ubuntu setup.

This is why I asked OP to run Gparted from a liveCD. That way we'll know if there are any NTFS partitions on there. ;)

---

### Post by pockets1 on 2011-01-08
I dont think I set the partition. there was something about this but I just hit next. it said something about windows at 150g and ubuntu at 80g

---

### Post by LetsMugSanta on 2011-01-08
Yeah I know I replied before your reply was posted. Use the Gparted tool

---

### Post by pockets1 on 2011-01-09
I can find all my windows file wile on ubuntu. is there anyway to get windows back or do a restore??

---

### Post by pockets1 on 2011-01-09
now all get is the grub rescue command.
Help

---

### Post by Bucky Ball on 2011-01-09
> **Bucky Ball said:**
> Boot ubuntu from the medium you installed it with (probably a usb dongle). Once you're at the desktop, find Gparted Partition Editor and look for an NTFS partition. If there isn't one, Windows has been wiped. Do this and get back to us. ;)

? Is it there?

---

### Post by pockets1 on 2011-01-09
i could not find the gparted tool. but i could see all my windows stuff. i was tempted to do the gateway restore where it would restore back to factory and put my files into a restore folder. now the only  that comes up is a grub rescue command.

---

### Post by Bucky Ball on 2011-01-09
You were tempted or you did it? Try and be a bit clearer. ;)

---

### Post by pockets1 on 2011-01-09
i got to the point where i had the option to to do a complete restore or a restore the os where it would put my files into a restore folder

---

