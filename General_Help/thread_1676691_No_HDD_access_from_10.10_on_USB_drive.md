---
title: "No HDD access from 10.10 on USB drive"
date: 2011-01-27
forum: General Help
---

### Post by Red October on 2011-01-27
Relative noob to Ubuntu here.

As i was a bit scared to attempt to partition my HDD in order to install Ubuntu, i purchased a USB drive and installed it there. So now if i boot without the USB drive plugged in it boots straight into XP as before. If i boot with the USB drive plugged in it boots to Ubuntu. Great, i'm happy with that - it would be nice for GRUB (on the USB drive) to give me the option to boot to XP on the HDD but i might explore that one some time in the future.

The problem i have is this - i used to boot from a 10.04 Live cd version installed on a USB memory stick and when doing this i could 'see' the HDD and access files on it (mp3s mainly). I should explain that the HDD is actually HDDs - there are two of them in a RAID 0 set-up - two 160Gb drives that appear as a single 320Gb c: drive under Windows. Under 10.04 there was a '316Gb File System entry'

Now, when i boot from the USB drive there's no trace of the HDD in 'places'. If i go into system/administration/disks i can see the two HDDs but all i can do is click on one of them and i can mount what i assume is a 4Gb recovery partition. The rest of the disk appears to be unformatted??? Please can someone help get my HDD access back!

Please let me know what additional information i need to provide ( i know there's bound to be some). Please also accept my apologies for any dodgy terminology i have used.

Red

---

### Post by amra.sonntag on 2011-01-27
I cannot give you a solution - but maybe point you in the right direction.

The problem begins with the way your Raid 0 works under Windows XP - i had it similar in a Raid 1 on an old box of mine. It probably doesn't actually use a real Raid device/controller on your motherboard, but some strange driver software to emulate the Raid behaviour. Those drivers are usally installed before installing the Windows OS and the whole setup is called Fake Raid. If you install Linux it will ignore those drivers and show your drives as they are.

However - i do believe Linux supports tools to mount your 2 harddrives into a Raid device. The mdadm package should provides those. It essentially creates a software Raid out of 2 disks or partitions of the same size. Maybe looking for mdadm guides and information on how to mount an existing filesystem you can figure it out. But to be honest - i would be afraid to destroy my Windows filesystem in the process. (but if the life cd could do it - it should be possible for you to do it too!).

---

### Post by Red October on 2011-02-03
So has 10.10 changed from 10.04 in this respect? As i said, if i boot from USB memory stick that contains the 10.04 live CD software, it 'sees' the HDD in 'places'.

---

