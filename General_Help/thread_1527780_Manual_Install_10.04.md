---
title: "Manual Install 10.04??"
date: 2010-07-09
forum: General Help
---

### Post by ve2 on 2010-07-09
Ok so I have a 1TB drive and I also have a 1TB drive with windows xp istalled. I need to know how to install Ubuntu manually. I have 4gb RAM and need to know what I should create 1st. The swap or the root? And do I need a home partiton? Plus the boot loader will install on the windows drive. So I guess to avoid any issues, I should copy the windows hard drive to make sure if I re-install with a drive image, Ubuntu will boot. Or I will have to to sudo the grub install... well back to my question. What are the ideal values.

---

### Post by bobcollard on 2010-07-09
> **ve2 said:**
> Ok so I have a 1TB drive and I also have a 1TB drive with windows xp istalled. I need to know how to install Ubuntu manually. I have 4gb RAM and need to know what I should create 1st. The swap or the root? And do I need a home partiton? Plus the boot loader will install on the windows drive. So I guess to avoid any issues, I should copy the windows hard drive to make sure if I re-install with a drive image, Ubuntu will boot. Or I will have to to sudo the grub install... well back to my question. What are the ideal values.
The simple answer is to let the installer for Ubuntu install side by side with the Windows system.  It will both partition and format the drive automatically.

---

### Post by ve2 on 2010-07-09
I thought about that... but I have an extra drive that I want to use for Ubuntu only. Need ideal manual set-up :):popcorn:

---

### Post by bobcollard on 2010-07-09
> **ve2 said:**
> I thought about that... but I have an extra drive that I want to use for Ubuntu only. Need ideal manual set-up :):popcorn:
See this link:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by ve2 on 2010-07-09
Great thank you! Now if I choose to not install the bootloader on the windows hard drive.. will Ubuntu detect windows if I change disk boot order in the bios?

---

### Post by audiomick on 2010-07-09
You should indeed look through the link that bobcollard posted.

The way you want to install is easy to do. You just need to choose the manual option when the installer gets up to the partitioning stage. If you want suspend to work, your swap needs to be a bit bigger than your RAM. The system itself needs a bit less than 4GB, so if you make your / partition 10 - 15 GB, you should be right for a while ( mine is up to about 7GB after 3 years). You don't need a separate /home partition, but there is a lot to recommend having one. If you need to re-install the system, you can just remount the /home partition and carry on where you left off. You can give /home the rest of the space on the drive, or keep it small too and make a dedicated Data partition, which can also be NTFS so that it is accessible from windows too.

I don't know enough about the consequences of where you put the boot loader to offer any advice. Sorry... :)

---

### Post by ve2 on 2010-07-09
thats good info! Does it matter which one I create 1st? The swap or the Ubuntu ext3 partition?;)
 
Plus do I make the swap logical or primary? OR both primary... does this make any difference?

---

### Post by audiomick on 2010-07-11
Don't know if you are still waiting for answers on this, but anyway:

> **ve2 said:**
> thats good info! Does it matter which one I create 1st? The swap or the Ubuntu ext3 partition?;)
 
When you come to do it, you will see that this question is a bit redundant. Whether you create the partitons first, or create them during the install, the process is effectively all one operation. You do have to specify the partitions one at a time, but you only press the "go and do it now" button once.


> Plus do I make the swap logical or primary? OR both primary... does this make any difference? Apart from the restriction that any Drive can only have 4 primary partitions (regardless of which OS. It is an old Hardware related restriction), it doesn't matter for a Linux system if the partitions are logical or primaries. Windows, on the other hand, has to be in a primary consideration.

The main consideration, as far as I see it, is to always leave yourself the possibility to change the partitioning with a minimum of effort. This means, if you already have 3 primaries on the drive, make the last one an extended so that you have to possibility to add logical partitions later if you want to.

---

### Post by ve2 on 2010-07-11
I'm always seeking input. Great help! txs!!!

---

