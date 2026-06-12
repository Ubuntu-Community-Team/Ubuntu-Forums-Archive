---
title: "how to fully install Ubuntu 11.10"
date: 2012-03-25
forum: General Help
---

### Post by Mshoory on 2012-03-25
[SIZE=2]hello, how to install fully Ubuntu 11.10 -64-bit, regular installation side by side to windows does not give the full performance.

i dedicated 150 GB to Ubuntu, but when i install I choose the partition i can choose 30 GB max, why not 150 GB

sorry i'm new to ubuntu world. 
[/SIZE]

---

### Post by techunit on 2012-03-25
> **Mshoory said:**
> [SIZE=2]hello, how to install fully Ubuntu 11.10 -64-bit, regular installation side by side to windows does not give the full performance.

i dedicated 150 GB to Ubuntu, but when i install I choose the partition i can choose 30 GB max, why not 150 GB

sorry i'm new to ubuntu world. 
[/SIZE]
Well lets see if I can bring things into light. First a few questions.
1. What did you used to partition your Windows Partition to free up space?
2. What are you trying to do? It isn't clear whether you want to install Ubuntu as your only, or dual boot.
3. What makes you believe that the install side by side function will not work? did you allocate space and the try to do the install side by side? If you allocated space to Ubuntu before attempting the install you need to do a manual partition during installation where you can select to install Ubuntu on that partition.
    You will need to set that partition to the ext4 format, and set the boot point to / then set it to use almost all of that space for Ubuntu, and set aside at least 4gb for a swap partition.

I hope this helps.
webupd8 did a feature on dualbooting in layman's terms [here]("http://www.webupd8.org/2011/09/dual-booting-guide-pdf-windows-and.html")

---

### Post by Mshoory on 2012-03-25
> **techunit said:**
> Well lets see if I can bring things into light. First a few questions.
1. What did you used to partition your Windows Partition to free up space?
[COLOR=Red]the one implemented in windows, i made partition with 150 GB[/COLOR]
2. What are you trying to do? It isn't clear whether you want to install Ubuntu as your only, or dual boot.
[COLOR=Red]dual boot[/COLOR]
3. What makes you believe that the install side by side function will not work? did you allocate space and the try to do the install side by side? If you allocated space to Ubuntu before attempting the install you need to do a manual partition during installation where you can select to install Ubuntu on that partition.
    You will need to set that partition to the ext4 format, and set the boot point to / then set it to use almost all of that space for Ubuntu, and set aside at least 4gb for a swap partition.
[COLOR=Red]I will do it, ext4, hope it works[/COLOR]

I hope this helps.
webupd8 did a feature on dualbooting in layman's terms [here]("http://www.webupd8.org/2011/09/dual-booting-guide-pdf-windows-and.html")


thank you

---

### Post by garvinrick4 on 2012-03-25
A Wubi install only allows 30 gig tops I believe you are using WUBI which is different
from a partition install which you want. 
Put CD in tray and then reboot and you will get a install or Try Me page. Make sure
CD is choosen first in boot sequence in your BIOS of computer.

##Happens to a lot of new users you put CD in tray and open it and a WUBI installer is there and when you click on it you start to install
but with 30 gig max. Here is link to tell you about it.
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide#Introduction")

---

