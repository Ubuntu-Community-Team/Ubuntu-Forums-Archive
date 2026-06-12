---
title: "from 11.04 to 10.04"
date: 2011-06-28
forum: General Help
---

### Post by shad0w7 on 2011-06-28
I currently have  a dual booting system with windows 7 and ubuntu 11.04. i hated the latest version of ubuntu and i am going back to 10.04. so if I reinstall 10.04 on the same old partition of 11.04 everything should be working ok right?

---

### Post by varunendra on 2011-06-28
> **shad0w7 said:**
> I currently have  a dual booting system with windows 7 and ubuntu 11.04. i hated the latest version of ubuntu and i am going back to 10.04. so if I reinstall 10.04 on the same old partition of 11.04 everything should be working ok right?
Absolutely right! Just go with default options and choose to format the partition while installing.

I am assuming that you have the same installation CD for 10.04 which you have tried successfully before. If not, try it in live mode beforehand to see if you don't hate it too. :)

---

### Post by nomko on 2011-06-28
> **varunendra said:**
> Absolutely right! Just go with default options and choose to format the partition while installing.
 
Wrong! The new installation (10.04) will overwrite the bootloader which also contains an entry for Windows. So, after the installation only Ubuntu will be visible in the bootloader. Best to do: after the installation open a terminal and execute the following command:```
grub-update
```
 
With this command, grub will restore all entries, Linux as well Windows. You can read here more about Grub with a dualboot system: [https://help.ubuntu.com/community/DualBoot/Grub](https://help.ubuntu.com/community/DualBoot/Grub)
 
 
Downgrading from 11.04 to 10.04 might also result in file version conflicts. BEst is to format the partition where 11.04 is installed on before installing 10.04. And be aware: always backup your important files!

---

### Post by varunendra on 2011-06-28
> **nomko said:**
> Wrong! The new installation (10.04) will overwrite the bootloader which also contains an entry for Windows. So, after the installation only Ubuntu will be visible in the bootloader.
Oh lemme see.... hmm.. I must be missing something here, could you be kind enough to explain it to me please :[INDENT]what happens when someone makes a 'fresh install' of ubuntu - in a formatted partition - on a system on which another OS already exists on another partition??

and..

what kind of installation would you consider it when someone boots off a cd, formats a partition, and installs the OS on it - fresh (or clean) install I guess?? Please confirm. :)

[/INDENT]I think you are right, but for the case when someone 'only' restores grub, not when a full installation is performed.

But anyway, keeping **update-grub** in mind is not bad.

Cheers!!


**_EDIT_:**

I apologize to nomko. After reading my own post, it seemed as if I was trying to insult him. To be honest, I was just trying to sound 'extra-funny'. Sorry for that. Actually that was a mistake which even a grub-expert could make if his mind is not fresh and alert.

---

### Post by coffeecat on 2011-06-28
> **nomko said:**
> Wrong! The new installation (10.04) will overwrite the bootloader which also contains an entry for Windows. So, after the installation only Ubuntu will be visible in the bootloader.

@nomko, this is not so. If the OP does a fresh installation of 10.04 using the previous 11.04 partition, then the 10.04 installer will indeed overwrite the mbr and the boot sector with its own (slightly earlier) version of grub2. However, the installer will also run os-prober, detect the presence of Windows and set up a dual-boot grub menu for Windows and Ubuntu 10.04.

---

### Post by bootedguy on 2011-06-28
If you hate 11.04 because of Unity, you can change to the classic version and still use 11.04.  Just change the settings for the Login Window.

---

### Post by nomko on 2011-06-28
> **coffeecat said:**
> @nomko, this is not so. If the OP does a fresh installation of 10.04 using the previous 11.04 partition, then the 10.04 installer will indeed overwrite the mbr and the boot sector with its own (slightly earlier) version of grub2. However, the installer will also run os-prober, detect the presence of Windows and set up a dual-boot grub menu for Windows and Ubuntu 10.04.
 
Ok, didn't realised that!

---

### Post by poliltimmy on 2011-06-28
> **bootedguy said:**
> If you hate 11.04 because of Unity, you can change to the classic version and still use 11.04.  Just change the settings for the Login Window.

I hate 10.04.2 and 11.04. Loved 10.04 on an upgrade, then with the last updates it will not boot right. Little round activity ball stuck in corner on desktop. 11.04 same thing even in a live session. Had to go back to 9.10 to get a working desktop. I can't even get Debian liveCD to boot and it supposed to be the stable one. Go figure. No current distro will boot. 

After waiting and talking to myself for a month ([http://ubuntuforums.org/showthread.php?t=1771263](http://ubuntuforums.org/showthread.php?t=1771263)), I am very frustrated. 

Blame nvidia, right. Why should I do that when I had a perfectly working desktop with 10.04.1 (through Upgrade) and all hell broke loose when the updates made my version 10.04.2. 

The pisser of all this is that I was booting my box to show an XP user that he could use Ubuntu instead of paying for an upgrade. When I booted up popped the up date manager. I installed the updates. I always reboot afterwards (old habits die hard). And the box took several Hard reboots after freezing on the slash screen, just to have the activity indicator lock in the upper left hand corner. He asked "Why not just backup to before the updates?) What could I say? 

Needless to say he just spent the money I tried to save him.

---

