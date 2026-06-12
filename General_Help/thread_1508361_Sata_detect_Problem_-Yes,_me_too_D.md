---
title: "Sata detect Problem -Yes, me too :D"
date: 2010-06-12
forum: General Help
---

### Post by Pyridox on 2010-06-12
Im having a smiler problem to many people installing Ubuntu 10.04 for the first time
My brand new sata2 seagate barracuda 250gig is not being detected by the installer on live CD.

Its a 100% blank store bought drive. so there is no raid on it.

Ive tried to replace "splash" in the boot line during cd startup with pci=nomsi, however this didnt help.

I also used the terminal to apply "sudo apt-get remove dmraid" again, nothing .
The drive is not being detected in the installer or by any means in Ubuntu(live cd).
Ive invested 10 hours into research and i wouldn't ask a question i haven't first done my homework on. so now im needing the help of a pro. Keep in mind that im new to Ubuntu and Linux. But we all start from some where. :D

Bios is detecting the hard drive and it is properly being represented pre-cd boot.
Perhaps im missing a bios setting that is Key to the Ubuntu sata interaction, but i dont believe this is the case. Its also important that i note when i said i replaced "splash" with "pci=nomsi" that i might not have a clear idea of what im doing. pressed any key during cd boot. hit f6 . then Esc. And just rplaced the splash directly. It was suggested on many forum sites to do this, but im not seeing the same result.

Please help :D
P.S.- Pretend i know nothing, its not far from the truth.

---

### Post by dcstar on 2010-06-12
> **Pyridox said:**
> Im having a smiler problem to many people installing Ubuntu 10.04 for the first time
My brand new sata2 seagate barracuda 250gig is not being detected by the installer on live CD.
.......

Boot the Live CD, run gparted and put a new Partition Table on the drive.

Then start the installation process.

---

### Post by Pyridox on 2010-06-13
Thank you for your reply however Gparted is not seeing my drive

---

### Post by Pyridox on 2010-06-13
Anyone know if there is a way that i can do a formate and fix my problem?

---

