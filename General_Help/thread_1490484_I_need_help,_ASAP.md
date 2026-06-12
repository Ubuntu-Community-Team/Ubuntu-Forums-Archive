---
title: "I need help, ASAP"
date: 2010-05-22
forum: General Help
---

### Post by Sorryunlucky on 2010-05-22
Hello, I installed Ubuntu with Wubi and I installed it on my Primary C: and I get this everytime I reboot:
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

Everytime I reboot I see the same message, my Laptop won't work now. :(

---

### Post by inso_741 on 2010-05-22
You can use windows disk to repair bootloader
just boot with the disc and you will find the repair option 
or you could even install grub form the live cd.....

---

### Post by Randypan on 2010-05-22
Have you tried booting from your Windows CD and try to repair your installation. Windows CDs of any recent release should contain some form of "repair Windows installation" Software. I don't know much more about it -having never faced this situation myself,  but I hope this gives you a direction towards resolving this issue. Also, you should state the version of Windows you are using as it will be probably needed by people who will help you through this thread.

Coming to think of it, this seems to be a Windows-specific issue, you should also try and seek help at some Windows support Forum.

[EDIT] To the poster above: Sorry for the duplicate answer. Your post was submitted as I was typing mine.

---

### Post by sanderd17 on 2010-05-22
If you didn't backup your data, use the ubuntu live CD to backup it before you use the windows recover CD. The second CD might delete everything when it doesn't find a windows installation.

---

### Post by Sorryunlucky on 2010-05-22
> **Randypan said:**
> Have you tried booting from your Windows CD and try to repair your installation. Windows CDs of any recent release should contain some form of "repair Windows installation" Software. I don't know much more about it -having never faced this situation myself,  but I hope this gives you a direction towards resolving this issue. Also, you should state the version of Windows you are using as it will be probably needed by people who will help you through this thread.

Coming to think of it, this seems to be a Windows-specific issue, you should also try and seek help at some Windows support Forum.

[EDIT] To the poster above: Sorry for the duplicate answer. Your post was submitted as I was typing mine.

I uninstalled Windows installing Ubuntu....
So I can't do that. And I came on here because it's a Ubuntu problem I have after I installed it... :/

---

### Post by inso_741 on 2010-05-22
how did you uninstall windows? 
you probably just formated the windows partition
which messed up your bootloader
what you can do now is install grub(GRand Unified Bootloader)
its better than windows' bootloder
follow [this]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7") guide to install grub form step 2
you must be very clear when you specify the partitions if you get confused you can always come back here....:P

or the easy way is to reinstall ubuntu from the live cd

and its not a ubuntu problem...you just messed up your bootloader
but don't worry we'll help you

---

### Post by Nythain on 2010-05-23
if you dont have windows installed anymore, you should probably re-install ubuntu with an actual ubuntu install cd... there's no verification that your wubi install will still even exist (doesnt wubi do some funky stuff with creating a virtual partition inside of the primary windows partition?) wich could be the problem to begin with

---

### Post by inso_741 on 2010-05-23
> **Nythain said:**
> if you dont have windows installed anymore, you should probably re-install ubuntu with an actual ubuntu install cd... there's no verification that your wubi install will still even exist (doesnt wubi do some funky stuff with creating a virtual partition inside of the primary windows partition?) wich could be the problem to begin with

I assumed that he installed ubuntu on a different partition altogether....it would be silly to format the partition on which ubuntu is installed from inside ubuntu

---

### Post by Sorryunlucky on 2011-01-05
Solved now. Finally got Ubuntu 10.10 I had Ubuntu 10.04 not long after this post I fixed it. 

Sorry for late reply guys.. Also thanks for the help.

---

