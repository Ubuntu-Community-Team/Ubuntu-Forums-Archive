---
title: "Too long to boot"
date: 2010-07-28
forum: General Help
---

### Post by suyash01 on 2010-07-28
Hi,
I just made a new install of 10.04. I has an older installation of 10.04 and it is still listed in grub.
But after I select the linux kernel to boot from grub, a screen with a blinking prompt appears and stays for 3 mins. After that everything is fast .
I don't understand why this screen is taking forever. 
Please help me get rid of this problem.
-Suyash

---

### Post by chopinhauer on 2010-07-28
> **suyash01 said:**
> 
I don't understand why this screen is taking forever. 


While the splash screen is showed, Ubuntu is loading the system under the hood.

If you post the characteristics of your hardware it will be easier to tell if this delay is normal or not. You can also stopwatch your boot time.

---

### Post by Zorgoth on 2010-07-28
Can you press F12 or something like that (I don't know if you should be able to, I haven't had to deal with anything like this in Ubuntu specifically) to get a more detailed view of what is going on?

---

### Post by dragos240 on 2010-07-28
You can also remove the quiet boot option for detailed results.

---

### Post by suyash01 on 2010-07-28
As I mentioned earlier , I had a previous install of Lucid which would be up and running in less than 30 seconds. This is some software problem.It is getting stuck somehwere.
It cannot take so long on any hardware.

specs:
Core 2 Duo at 2.4Ghz
2 GB DDR2
1 TB SATA 2
240 GB SATA 2
Nvidia 8400

---

### Post by dragos240 on 2010-07-28
I suggest booting up with F12.

---

### Post by suyash01 on 2010-07-29
> **dragos240 said:**
> I suggest booting up with F12.
F12 not working. Nothing happens on pressing it.
Please suggest something else. Its a crazy boot-up time.

---

### Post by suyash01 on 2010-07-29
Hi,
 I would like to add a few details which might help in diagnosing this problem.
I had originally 3 hard-disks: 80 GB PATA, 160 GB SATA, 1TB SATA.
I had originally installed XP on 80 GB about 7 years ago. Win 7 was installed on 160 Gb one and sometime back Ubuntu on 1TB hd. 
Now the master hard disk was the 80 gb one. But yesterday it seemingly crashed as the system(hardware) doesn't start if I connect the 80 gb hd. Since the MBR was located on this hd , naturally the bios couldn't find Grub or any OSs to boot. 
I used the live cd to install ubuntu once more on a new partition on 1Tb hd and the grub installed on 160gb hd. the home partition was specified as another separate partition on 1 Tb hd. 
The old ubuntu installation and old home folder still resides on 2 separate partitions on 1Tb hd (different from the 2 partitions of the new install of ubuntu).

---

