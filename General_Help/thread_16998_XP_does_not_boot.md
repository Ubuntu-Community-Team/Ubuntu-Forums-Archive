---
title: "XP does not boot"
date: 2005-02-25
forum: General Help
---

### Post by StefanoCole on 2005-02-25
Hello, I have an hard disk in which was originally installed Windows XP Pro. With Partition Magic 8.0 I have added 2 partitions to the hard disk: 1 ext2, 1 Linux swap.
Then I have installed Ubuntu "The Warthy Warthog". Installation went fine.
Now, when I power on Grub gains control. If I select Ubuntu no problems, but if I select Windows XP from the Grub menu here is what happens:
Windows XP seems to start since I can see the starting logo, then, after a few seconds a blue screen appears and the following message appears: Autocheck program not found. At this point the system restarts. So I am not able to enter in Windows any more. I have checked the menu.lst file but it looks o.k. since it contains the following:

title Windows
rootnoverify (hd0,0)
chainloader +1
makeactive

Can you help me?  :sad: 
Thanks in advance for any help!

Stefano

---

### Post by valter on 2005-02-26
I think that your Partition Magic did something bad, but I am not an expert. I use dual boot myself but I first partitioned the disk, then installed Windoza and then Ubuntu - works well. Maybe you can fix it whith Windows repair (from your Win cd), but I am not sure it doesn't rewrite MBR

---

### Post by abovett on 2005-02-26
Hi

When you partitioned the disk, what order did you create the partitions in? Windows XP does not like being moved to a different partition as it references the absolute partition number when booting. Your grub menu file says WIndows is the first partition - is that still the case?

You should be able to fix the bproblem from the XP recovery console, or with a ""Repair install" of XP. However, make sure you have a boot disk or something to get back into Linux as Windows has a habit of taking over.

Cheers

Andy B

---

### Post by ThePainter on 2005-02-27
Hi,
I have fiddled about a bit with dual boot a bit and have found a few things that dont work.
I have two HD's.

With Mandrake I could put XP anywhere and it would find it and boot but with UBUNTU for some reason it likes XP to be a the beginning of the Master drive anywhere else and it just errors on boot.

I have all ntfs on the master and ext3, swap and Fat32 on the Slave and it works OK.

If yours shows the XP start screen then grubs is OK because it is getting into the system so the problem is with your system and not the grub.
If you replace the MBR with the XP disc you will not repair your system but if you use that to do a repair install then you will have to run the recovery part of the UBUNTU disc to reinstall the grub.

Good Luck.

---

### Post by allans on 2005-02-27
Sorry if this sounds really patronising, but your boot menu.lst for windows should have the boot option on the end of it.

---

### Post by StefanoCole on 2005-02-28
For abovett: XP is installed in the first partition of the hard disk and it is the original partition.
I have made an Ubuntu bootable floppy disc and I will try to fix the boot problem from the XP recovery console.

Thanks a lot, Stefano

---

### Post by bored2k on 2005-02-28
xp does not boot... is this necessarily a problem ???  :-s

---

