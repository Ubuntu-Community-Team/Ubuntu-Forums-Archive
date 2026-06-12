---
title: "Can't Boot into Windows 7"
date: 2010-03-11
forum: General Help
---

### Post by mmmg on 2010-03-11
Today I was messing around with my partitions, and I decided to shrink my main partition that had Windows on it, so that I would could have one big storage partition and then a Windows 7 one and a Ubuntu one. Well, it didn't really work so I decided just to wait for Lucid to come out and start with a fresh install. So I went into EASEUS Partition Manager and resized my main Windows 7 partition back to its normal size. It had to reboot and did its stuff, and then when I restarted my computer, grub was showing the grub rescue> thing. So I went into the Windows 7 recovery disk, and tried all the BootRec.exe options. None of those worked. So I decided to go to the extreme and just delete Ubuntu completely. I hadn't really done anything with it yet so it wasn't a big deal. I deleted the entire partition with GParted and then resized the main partition all the way. Then I booted into a Ubuntu live usb and re-installed Ubuntu. I thought it would just reinstall Grub and I would be able to get to both Ubuntu and Windows 7. It did install Grub, but now I can only boot into Ubuntu. It's really weird, because I can boot into windows, it just says starting windows and does the loading thing. And then EASEUS Partition Manager comes and says that all resize operations were complete successfully(because I hadn't booted into windows since I resized stuff with it) and then the screen just stays black for a long time. I don't know what to do.

Thanks in advanced.

EDIT: If I wait long enough, my computer just reboots...

---

### Post by prodigy_ on 2010-03-11
Resizing a partition is usually a bad idea. Especially if it's a system partition. 

If you have a backup of your data, the best thing is - obviously - to reinstall from scratch. If you don't have a backup, boot into Ubuntu Live CD and see if your Windows is readable at all. If you can access it, you can probably copy everything you need to some safe location (to another HDD or to a flash drive) and then reinstall whatever OS you want.

---

### Post by Mark Phelps on 2010-03-11
If you've tried all the Startup Repair options from your Win7 repair CD/install DVD, there's really little else you can do other than back up your files and reinstall.

If you used the Ubuntu installer or GParted to shrink your Win7 install, next time, check these forums before doing something drastic like partition work.  There have been LOTS of posts here advising folks NOT to do that and to use the Win7 Disk Management utility instead.

---

### Post by mmmg on 2010-03-11
Somehow it's working. I have no Idea how or why, but it is. I must of tried booting into Windows six times last night. Today, I got home from school, and tried again, and it worked fine. It's a mystery. I didn't change anything. Oh well though.

---

