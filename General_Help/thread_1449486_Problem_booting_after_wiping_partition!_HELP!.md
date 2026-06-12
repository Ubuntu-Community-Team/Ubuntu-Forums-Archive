---
title: "Problem booting after wiping partition! HELP?!?"
date: 2010-04-07
forum: General Help
---

### Post by AlecMayhugh on 2010-04-07
I wiped the partition that had the Ubuntu 10.04 beta installed on it and now everytime i boot up i cant get into windows because it says,
''GRUB rescue 
ERROR NO SUCH PARTITION''
And i dont know what to put into the prompt to boot into windows. WHAT DO I DO???

---

### Post by uberlube on 2010-04-07
try super grub disk

---

### Post by AlecMayhugh on 2010-04-07
> **uberlube said:**
> try super grub disk

Whats that? Sorry, ive been using Apple products my whole life so im new to linux :/

---

### Post by uberlube on 2010-04-07
its a grub recovery disk, its pretty intuitive. a quick google will lead you to it and its quite well documented.

---

### Post by metalf8801 on 2010-04-07
you can find super grub disk here
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

also do you have a Windows CD? if you should try to repare your system using the fixmbr command 

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)


oh also installing Ubuntu 9.10 where 10.04 beta was might fix things 

are you still using a version of Ubuntu on this computer? 

I hope this helps if it doesn't post again 
Dan

---

### Post by AlecMayhugh on 2010-04-07
It wont let me boot straight up Vista, its making me go to the system recovery when i hit detect any OS

---

### Post by wilee-nilee on 2010-04-07
So your problem is that you need to load the vista bootloader to the MBR, here is a vista recovery disc link.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Go to a vista forum if you don't get the correct answers here, there are a lot of knowledgeable people but a google search for loading the vista bootloader is only a few clicks away, here is one but make sure you know what your doing.
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Vista is reachable with a live Ubuntu Cd if you need to pull anything out for backup.

You could also have Vista back but just installing another version of Ubuntu in a small partition, grub would see Vista.

Do you have a vista install DVD or whatever it installs with?

---

