---
title: "hardrive mbr corrupt?"
date: 2011-03-21
forum: General Help
---

### Post by jonnyboysmithy on 2011-03-21
My friend has a 1.5TB hard drive in her computer and its recognized as a 500gb one.
This has been happening since they configured something with grub, this was a while ago so we don't know exactly what we did. 
you can still browse the drive but not all the files that should be there are there, and if they are there a lot are just not the size they used to be.
I'm not sure if the disk is ext3 or ext4 I don't have it here at the moment though..
The data on it is very precious.
Any ideas on any software utilities we could try?

---

### Post by jonnyboysmithy on 2011-03-21
by the way we have cloned the drive so we can experiment on that

---

### Post by arvevans on 2011-03-21
Probably not associated with MBR, as that is used for booting or to re-direct booting to a boot segment on another partition.

My guess (only a guess) would be to make a backup of what files you can access.  Then reboot and do file system check (fsck) from the boot menu.  First do fsck to see what it finds, then if it seems advisable do fsck with the "fix" option to repair your file system.

Others lurking here may have more and better ideas?

---

### Post by jonnyboysmithy on 2011-03-22
I hope that works..
I'll try that next time I see 'em
If that doesn't work I don't know what will...

---

