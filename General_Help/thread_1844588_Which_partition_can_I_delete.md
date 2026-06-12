---
title: "Which partition can I delete?"
date: 2011-09-15
forum: General Help
---

### Post by not_the_geekiest on 2011-09-15
I would like to install windows 8 onto my computer however, my computer al ready has 4 partitions. Can someone recommend which one I can delete without doing (that much) damage?

[http://i56.tinypic.com/1zgxdzb.png](http://i56.tinypic.com/1zgxdzb.png)

I am debating between recovery or system (I have grub).

---

### Post by FormatSeize on 2011-09-15
Windows 8 is out already?
 
Anyway, I would recommend deleting the ntfs partition dev/sda2, then install Windows 8 in the free space created. The system partition is far too small for just about any operating system, and you would want to hold on to the recovery partition in case something goes wrong and you need to restore Windows in the state that it's in now. 
 
 
Lastly, I don't think that this is the right place for this, but one of the higher-ups will get it moved to the correct place.

---

### Post by raja.genupula on 2011-09-15
by using gparted you can delete or make some free space with out any damage to your data . 
try this 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Synoc on 2011-09-15
warning, installing Windows tends to trash the MBR, you'll need to fix it to see your ubuntu again (most likely, haven't tried with 8) and Windows 8 is out in a lmited form as a beta for developers, last I heard and it's SUPPOSED to be pretty good (for Windows).

---

### Post by Alan F on 2011-09-15
If you delete sda1 or sda2 you will lose Windows 7
If you delete sda3 you will lose the Recovery facility
If you delete sda4 you will lose Ubuntu

I assume that you wish to preserve all

I suggest the following

You probably do not actually need Recovery at this moment so backup this partition, sda3, using something like Paragon Backup in Windows to an external hard disk. Then delete sda3

Move sda4, Ubuntu, into unallocated space between sda2 and sda4. This will leave about 36GB unallocated space at end of drive. Create 4th partition in that space install Windows 8 here then repair Grub in Ubuntu.

---

### Post by not_the_geekiest on 2011-09-16
> **Alan F said:**
> If you delete sda1 or sda2 you will lose Windows 7
If you delete sda3 you will lose the Recovery facility
If you delete sda4 you will lose Ubuntu

I assume that you wish to preserve all

I suggest the following

You probably do not actually need Recovery at this moment so backup this partition, sda3, using something like Paragon Backup in Windows to an external hard disk. Then delete sda3

Move sda4, Ubuntu, into unallocated space between sda2 and sda4. This will leave about 36GB unallocated space at end of drive. Create 4th partition in that space install Windows 8 here then repair Grub in Ubuntu.

Thank you. I followed your suggestion and it worked well.

---

