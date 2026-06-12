---
title: "help with uninstalling ubuntu"
date: 2011-06-22
forum: General Help
---

### Post by heyaheyhey on 2011-06-22
So i recently got ubuntu to try it out thougt that i would like it but after i installed it i deceded i didnt want i i go to unistall it and format the drive. well now i have this error with grubb loader and i cant boot up windows 7 now. Idk what to do and i dont have a windows 7 disk because it was preinstalled on my labtop. I would love to get it up and working but idk how. please help many thanks

---

### Post by haqking on 2011-06-22
> **heyaheyhey said:**
> So i recently got ubuntu to try it out thougt that i would like it but after i installed it i deceded i didnt want i i go to unistall it and format the drive. well now i have this error with grubb loader and i cant boot up windows 7 now. Idk what to do and i dont have a windows 7 disk because it was preinstalled on my labtop. I would love to get it up and working but idk how. please help many thanks

you want to get windows 7 up and running or ubuntu ?

---

### Post by heyaheyhey on 2011-06-22
i want to boot windows 7. I had a 250 gb hard drive i partitiond and installed ubuntu onto that other partition. but now i cant get windows 7 to boot and the only way i can get ubuntu to work is by loading it with the usb loader. But i want ubuntu gone.

---

### Post by haqking on 2011-06-22
> **heyaheyhey said:**
> i want to boot windows 7. I had a 250 gb hard drive i partitiond and installed ubuntu onto that other partition. but now i cant get windows 7 to boot and the only way i can get ubuntu to work is by loading it with the usb loader. But i want ubuntu gone.


Sounds like the correct process for removing Ubuntu with W7 installed wasnt adhered to which can screw up your grub.

I am guessing you dont have a Windows repair disk to boot to ?

try the suggestions from the bottom post on this thread:

[http://ubuntuforums.org/showthread.php?t=1685389](http://ubuntuforums.org/showthread.php?t=1685389)

hope it helps

---

### Post by Robert Finley on 2011-06-22
If you are prepared to completely format the drive, then when you reinstall from the windows cd is should put it's own bootloader over grub.  I have experienced a problem with this senerio trying to reinstall from factory backup media, where it installs the system but not the boot loader.  I even tried the windows 7 rescue disk and it didn't fix it.

Honestly what I did was download a pirate bay edition of windows 7 which installed fine though it knew it was a pirated copy. I didn't care though because once I installed it I simply removed it and reinstalled the factory backup again.  In effect I just used the Windows 7 CD to install the windows bootloader.  It worked though. Laptop is like new now..

I would LOVE to hear someone post a better way.

---

### Post by heyaheyhey on 2011-06-22
so i press shift right after bios. but it says to type stuff but idk which one.

---

### Post by WorMzy on 2011-06-22
[http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/)

You'll need to download a recovery disk, burn it to CD, then boot to it and repair the Windows bootloader. Ask on a Windows forum if you need help with this.

---

### Post by haqking on 2011-06-22
> **Robert Finley said:**
> If you are prepared to completely format the drive, then when you reinstall from the windows cd is should put it's own bootloader over grub.  I have experienced a problem with this senerio trying to reinstall from factory backup media, where it installs the system but not the boot loader.  I even tried the windows 7 rescue disk and it didn't fix it.

Honestly what I did was download a pirate bay edition of windows 7 which installed fine though it knew it was a pirated copy. I didn't care though because once I installed it I simply removed it and reinstalled the factory backup again.  In effect I just used the Windows 7 CD to install the windows bootloader.  It worked though. Laptop is like new now..

I would LOVE to hear someone post a better way.

I think you will find the condoning and use of Pirate software is forbidden (forum guidelines)

^incoming^ ;-)

---

### Post by Robert Finley on 2011-06-22
If you go read those old links you'll find microsoft has frozen all rescue disk downloads.  I couldn't find a working link anywhere.  That was part of my problem. And yeah, my bad, I don't really condone piracy but I guess I justified with the fact that I do OWN a windows 7 license and in the end the only software I ended up with was what I paid for..

---

### Post by Matt__ on 2011-06-22
like Robert says..all recover disk downloads frozen at the moment pending copyright enquiry.

sent you private mail to get a recovery disk.
do NOT support piracy, but rules may be bent occasionally

use this guide to repair 

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by mimistarshina on 2011-06-22
hey guys this is heyaheyhey had to login from dif username. I decided to reinstall ubuntu alongside windows 7 seeing as i still had it after i intsalled it the grub menu came back up and i am on windows 7 now. but i still want to get rid of ubuntu and the grub i dont have the disk seeing it came preinstalled on my comp. and it is taking up space apparenty it wanted to take like 50 gb and that is to much. so any ideas

---

### Post by haqking on 2011-06-22
> **mimistarshina said:**
> hey guys this is heyaheyhey had to login from dif username. I decided to reinstall ubuntu alongside windows 7 seeing as i still had it after i intsalled it the grub menu came back up and i am on windows 7 now. but i still want to get rid of ubuntu and the grub i dont have the disk seeing it came preinstalled on my comp. and it is taking up space apparenty it wanted to take like 50 gb and that is to much. so any ideas

well now you can make a repair disc from withint windows and then repair the MBR....though there are a few ways to do it, it would be good that you have a repair disc

---

