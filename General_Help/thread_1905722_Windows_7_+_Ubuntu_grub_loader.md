---
title: "Windows 7 + Ubuntu grub loader"
date: 2012-01-07
forum: General Help
---

### Post by Zero Hack on 2012-01-07
Windows 7 loader is broken.

How can I add my windows 7 that'll boot to grub?

It's stored on my C: drive in the folder "Windows" obviously :P.

Any help?

---

### Post by imachavel on 2012-01-07
well you can boot into Linux? grub 2 and windows grub seem to have a major issue getting along. I have had this problem and couldn't solve the issue and had to reformat. Ok but you could try the windows recovery console(boot to windows disk, second option recovery console, not the same option as windows repair, but repair windows recovery console)

fix mbr might reset the master boot record. I believe another command is more suitable for resetting the boot flag in grub. None of that worked for me, plus, it takes the risk that /dev/sda won't recognize windows master boot record. I was recently viewing on this forum that there is a very good linux live cd .iso you can download and burn to cd then boot from that will reset the whole grub parameter from some master programmer. Not sure how it works. I forgot the name also. Maybe one of the mods will drop by and check this thread soon and list what it is and how to use it. It is supposed to be a cd so simple that it does all the work for you and you just click 'repair grub'

was any of this helpful? No? sorry then

---

### Post by Mark Phelps on 2012-01-07
> **Zero Hack said:**
> Windows 7 loader is broken.

How can I add my windows 7 that'll boot to grub?

It's stored on my C: drive in the folder "Windows" obviously :P.

Any help?

NO, the Windows 7 Loader is NOT in the Windows folder.

You can try using Boot-Repair to see if it can restore Win7 boot capability:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by efflandt on 2012-01-07
Often Win7 boots from a different partition than you think it does.  It would have been nice to have gotten a snapshot of **sudo fdisk -l** before installing Ubuntu.

For example my Dell desktop had 3 partitions, Dell Utilities (small), RECOVERY, and OS.  It originally booted from sda2.  I used Win7's own Disk Management to shrink sda3 before installing 64-bit Maverick (10.10) on sda4 (no swap since I have 8 GB RAM) and I actually put grub on sda4, so I could simply change boot partition using standard DOS/Win mbr.  Although, I now boot everything including 64-bit 11.10 on sdb1 from its grub on sdb (SSD).

I learned that Dell booted from its RECOVERY partition after temporarily installing Ubuntu on a laptop I was setting up for someone and I had to jump through hoops (run Win7 system DVD) multiple times before I was able to repair it to to boot from sd3 after removing Ubuntu with grub on sda4.  I thought having grub on sda4 would make removal easier, but not when you pick the wrong partition afterwards to try to boot Win7.

But in either case, I never had any trouble booting Win7 from grub (except when I had grub in the mbr of my desktop and a Dell program, DataSafe I think, stored data in what it thought was an unused part of the mbr and it overwrote part of grub2 which is larger).  So you do have to be careful about Windows programs that may try to store data in the mbr area.

---

