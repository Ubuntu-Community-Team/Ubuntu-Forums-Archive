---
title: "Dualboot problem with existing Windows"
date: 2009-07-11
forum: General Help
---

### Post by gmbutler on 2009-07-11
This should be simple, but I can not get it to work.

I have googled, scoured the net, the forums and every obscure post I could read, but to no avail. Please follow carefully, as it gets a little confusing at times. Here's my situation.

I installed Ubuntu Jaunty on a primary master with another harddrive on the slave, which had an old Windows XP installed. Then I disconnected both, connected the Windows drive solo at the primary master and reinstalled Windows (this is now what I mean by existing OS). Then I reconnected the Ubuntu drive at the slave and added two more hard drives (via a SCSI controller card) that I use for storage.

Thus, at the moment Ubuntu is on the Primary *SLAVE* and Windows on the primary *MASTER*. After editing the menu.lst Ubuntu boots fine, but I can not get Windows to dual boot at all using grub, even if connected as slave. When booting via the BIOS boot menu, Windows does boot, but waiting to hit F12 every time is not as much fun as they make it out to be :lolflag:
I need to mention that due to time-pressing matters, I could not do a fresh install of Windows before I did the Ubuntu install. Now I have installed (by auto downloading via Add/Remove) GB's worth of apps and packages that I'll use for my designing business, as well as for some leisure, else I would just reinstall Ubuntu.

For reference, here are my current devices:

[INDENT]/dev/sda1 (hd0,0) - Windows[/INDENT]
[INDENT]/dev/sdb1 (hd1,0) - Ubuntu[/INDENT]
[INDENT]/dev/sdc2 (hd1,0) - Storage[/INDENT]
[INDENT]/dev/sdd1 (hd1,0) - Storage[/INDENT]

With this there are also 3 DVD writers installed which work fine.


Here is the my current menu.lst entry:

[INDENT]### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
rootnoverify (hd0,0)
chainloader +1
[/INDENT]

I eventually deleted the map commands totally after I moved Windows to the primary, as I don't see how it is needed when Windows is running from the primary partition on the primary master.

OK. So here are my options as I see it.
[LIST=1]
[*]**Option 1**: What must the correct menu.lst entry be to use the current setup without changing drives again? I have tried several different combinations and aren't reaaly in the mood to experiment with options. If you know what it must please post it, otherwise no suggestions please.

[*]**Option 2**: I must put Ubuntu on master and Windows on slave again. How do I then reconstruct the bootloader? Jaunty apparently doesn't support the command-line options from the live cd (read this on several threads)

[*]**Option 3**: WHat else am I to do?
[/LIST]

Now is probably a good time to mention that while I am not a newbe to pc's, I am not very familiar with Linux as a whole, and definitely not the command-line, having been a Windows user as long as I've been using pc's.

Michelle

---

### Post by zvacet on 2009-07-11
Let your Windows entry look like this 

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by gmbutler on 2009-07-12
Hi zvacet

Thanks for the reply. Nope, I just tried that and I get

[INDENT]Error 13: Invalid or unsupported executable format[/INDENT]

when choosing Windows from grub. I just realised now that I forgot to mention it in my post above (sorry for that), but I always got Error 13, with all the different options I tried. According to all the threads and documentation I read, your solution should work, but alas, no.

My only thought on this is that my grub is semi-broken, and needs to be fixed, but I do not know if this is in fact the case. I do not know what I should do now.

**PS:** :mrgreen: I see now that my devices above was also not given correctly. I don't know haw this happened, but here is the correct list:

[INDENT]/dev/sda1 (hd0,0) - Windows
/dev/sdb1 (hd1,0) - Ubuntu
/dev/sdc2 (**hd2,1**) - Storage
/dev/sdd1 (**hd3,0**) - Storage[/INDENT]

If this makes a difference, would you please adjust the grub entry?

---

### Post by northern lights on 2009-07-12
From within Ubuntu run```
sudo update-grub
```Now what?

---

### Post by gmbutler on 2009-07-12
northern lights

Thanks. Grub did update, but I still get Error 13.

---

### Post by northern lights on 2009-07-12
Wicked.

This error should only occur, if Windows is not the primary master, i.e. sda1.

Can you post the output of ```
sudo fdisk -l
```?

Thank you.

---

### Post by gmbutler on 2009-07-12
Here it is:
[INDENT] Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18791879

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd5b203a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9598    77095903+  83  Linux
/dev/sdb2            9599       10011     3317422+   5  Extended
/dev/sdb5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ae7d7fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90089840

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
[/INDENT]Hope this helps.

---

