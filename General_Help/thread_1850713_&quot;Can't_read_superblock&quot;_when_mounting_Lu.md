---
title: "&quot;Can't read superblock&quot; when mounting Luks Encrypted RAID volume"
date: 2011-09-27
forum: General Help
---

### Post by Kissell on 2011-09-27
This server has a ten disk software RAID-6 setup using mdadm.  The volume is a luks encrypted XFS partition.

After rebooting the RAID array starts up fine on its own, all disks are present and it is clean.  Also I'm able to use "cryptsetup luksOpen" to unlock the partition, the password is good, and it creates the device mapper.

So far, everything is normal, but when I try to run "mount" I can't mount the partition, it says "Can't read superblock".

This is something I have done thousands of times...  its not my commands (I checked against backups of scripts I made), something is wrong/broken...  

I really need to get access to this data.  Can anyone help me repair the superblock?

---

### Post by Kissell on 2011-09-27
I ran "xfs_repair" and it said it couldn't run without doing the "-L" option, which was really scary, because the help file says only to use -L as a last resort.  

Anyway, ran "xfs_repair -L /dev/mapper/Data" and it thought to itself silently for several long minutes...  but when it was done it had repaired the volume.

phew!

Now I get to revisit the famous old budget conversation where somehow me being the voice of reason ends up making me look like I don't know anything about computers.

ME: "We really need to backup that data"
BOSS: "We'll get a backup in the new budget cycle"
ME: "We almost lost all the data last night, we need it sooner"
BOSS: "Why did we almost lose the data"
ME: "I don't know, S-happens, that's why people normally make backups"
BOSS: I need to know more than S-happens, what went wrong?
ME: "The file system wouldn't mount, but it's anyone's guess as to why"
BOSS: (looks at me like I don't know how to use a mouse)

---

### Post by Kissell on 2011-09-27
NOTE: Just a reminder for anyone reading this in the future (probably myself)...  xfs_repair does actually work...  This isn't the first time I've resorted to it.

Also, on a luks encrypted RAID volume, remember NOT to run repair on the md device (i.e. /dev/md0).  That is not the xfs file system, the xfs file system is inside the encryption, so you have to run repair on the mapper device (i.e. /dev/mapper/Data).  I forgot that until I hit "ENTER" and quickly exclaimed "Oh foo bar" and hit CTRL-C...  Unfortunately in that order...  but luckily I caught it before any damage could be done.  This is potentially very dangerous, but theoretically xfs_repair shouldn't find a superblock and I'm guessing would hopefully abort without screwing anything up.  Luckily I caught it while it was still searching for the superblock, so I didn't get to find out what happens if I let it run.

---

