---
title: "pls help"
date: 2010-08-25
forum: General Help
---

### Post by garren06 on 2010-08-25
i am trying to format my hard drive so i can run ubuntu and windows and my laptop just won't let can someone pls point me how to do this 


thank you

---

### Post by snappy90 on 2010-08-25
do you have windows already installed???

if so boot a live cd of ubuntu and select install side by side and  choose at boot.

u might have to enable cd boot in your bios settings.  

hope that helps

---

### Post by howefield on 2010-08-25
Have you created an Ubuntu Live CD yet ?

If so, boot the computer with it to the desktop, (Try before installing) and go to System > Preferences > GParted. This application will allow you to manipulate your disk.

Remember to save any valuable data that may be on the disk before doing any work on it.

If you want some more information, try and be specific as to what you have already tried and where you are stuck.

---

### Post by garren06 on 2010-08-25
Right i have been running ubuntu for months now and love it BUT there are some things like gps blackberry,itunes  etc that won't work with unbuntu so i was going to format my hard drive and install windows xp and then install unbuntu 
thx

---

### Post by Rubi1200 on 2010-08-25
Guides that will help:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Good luck!

---

### Post by garren06 on 2010-08-25
> **Rubi1200 said:**
> Guides that will help:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Good luck!

Right i put window xp disk in and run it though and it can't find my hard driver BUT i can load ubuntu on my hard drive and runs great but i want to load window xp and then have ubuntu on it as well

---

### Post by snappy90 on 2010-08-25
you have to make sure the hard drive is formatted as NTFS i think that all windows will see for installation

i had a problem with that and it wanted it as NTFS

used Gparted from a live cd would be the best way to do it

---

### Post by snappy90 on 2010-08-25
i also suggest installing xp over the whole drive and then using the Ubuntu install to split the drive as installing windows over Ubuntu never seems to work for me.

---

### Post by davidmohammed on 2010-08-25
> **garren06 said:**
> Right i put window xp disk in and run it though and it can't find my hard driver BUT i can load ubuntu on my hard drive and runs great but i want to load window xp and then have ubuntu on it as well

If your hard-drive is SATA then windows XP will not install on it.  You'll need to slipstream the relevant SATA driver OR have a look in the bios to see if you can run your drive in "Compatible" or "IDE-compatible" mode.

---

