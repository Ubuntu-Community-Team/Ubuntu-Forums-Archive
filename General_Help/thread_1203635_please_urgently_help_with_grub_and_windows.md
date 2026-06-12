---
title: "please urgently help with grub and windows"
date: 2009-07-03
forum: General Help
---

### Post by vipulraheja on 2009-07-03
hi everyone
i wanted to dedicate more hard disk space to ubuntu and hence cleaned up the space in which ubuntu was installed using the disk management in windows vista. I was planning to install the newer version of ubuntu on the extra space that i created by deleting and merging my hard disk partitions. So in the process, i ended up removing the GRUB installed on the system. Now the moment my computer starts booting, it shows 
error 22 
and hence i'm unable to boot into windows also.

please help.

---

### Post by coffeecat on 2009-07-03
I presume you mean that now you have free unallocated space on your HD where Ubuntu once was, and that the Vista partition is untouched but you can't boot into it because grub stage 2 went with the Ubuntu partition.

You've got two options.

1 - Download [SuperGrubDisk]("http://www.supergrubdisk.org/") and use that to boot into Vista and/or restore the Windows MBR.

2 - Reinstall Ubuntu into your unallocated space, making sure the installer doesn't touch the Vista partition. A new Ubuntu installation will set up a new grub with a dual-boot menu for your Vista and Ubuntu.

**Edit:** by the way, if you use the Ubuntu live CD, you have a good graphical partitioner at System > Adminstration > Partition Editor for if you need to do any more partition work before installing. But don't use it to resize the Vista partition. You risk making Vista completely unbootable if you do that.

---

### Post by raymondh on 2009-07-03
If your final intention is to dual-boot, I would go with coffecat's #2 option.

---

### Post by ajgreeny on 2009-07-03
> **raymondhenson said:**
> If your final intention is to dual-boot, I would go with coffecat's #2 option.
+1.
If you did all this just to make more room for ubuntu 9.04, just get on and install it.  9.04 is the best version so far (for me at any rate) and there seems to be nothing that it can't do with my hardware, though I do have to ask sometimes, "how?".  There is no point downloading supergrub and fiddling with that if you are going to install another ubuntu straight after.

Just so you understand what happened, when you deleted the ubuntu partition you previously had, you also removed the **/boot/grub/menu.lst** file from that partition.  Grub on your windows MBR pointed to that file for its configuration information and to give you the grub menu, so without it, grub was totally useless, hence the error22.

---

