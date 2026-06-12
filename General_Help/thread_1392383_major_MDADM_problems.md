---
title: "major MDADM problems"
date: 2010-01-28
forum: General Help
---

### Post by valuntahr on 2010-01-28
I'm trying to rebuild 2 mdadm arrays that I lost the configs for when I uninstalled ubuntu trying to fix another problem. I initially didn't have any problems bringing the first array online. However, after installing a driver to bring the second batch of drives online and attempting to rebuild mdadm.conf I have somehow managed to lose the superblock information for all of the drives in both arrays. 

The arrays in question are 2 3 disk raid 5 arrays

Here are the commands that I've tried so far and their corresponding error messages: 

mdadm -assemble --scan 
```
mdadm: No arrays found in config file
```

mdadm --examine /dev/sdb
```
mdadm: No md superblock detected on /dev/sdb.
```
*repeat previous error messages for the rest of the drives in both arrays*

fdisk -l
```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e280

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2      121601   976752000   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c78cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      121601   976752000   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00035430

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2      121601   976752000   fd  Linux raid autodetect

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f3198

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008f357

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000336ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      182401  1465136001   fd  Linux raid autodetect

```

mdadm /dev/md0 --assemble --update=uuid
and
mdadm /dev/md0 --assemble --update=resync
```
mdadm: /dev/md0 not identified in config file.
```
*repeat error for /dev/md1*

Any help in solving this issue would be greatly appreciated

---

### Post by Fcon_Vpro on 2010-01-28
Have you tried assembling by specifically mentioning which drives 
ie: sudo mdadm --assemble /dev/md1 /dev/sda1 /dev/sdb1 /dev/sdc1
Or if that doesnt work then try using --assemble --force

---

### Post by valuntahr on 2010-01-28
mdadm --assemble --force on both arrays errors out with a no recognizable superblock error. Is there any way to rebuild the superblocks without wiping out the data on the arrays?

---

### Post by falconindy on 2010-01-28
Not sure what else I can add to this except that order matters when reassembling arrays without a config file. This is physical order, not necessarily reflecting the /dev/sdxy naming scheme (which may change).

If the above doesn't make sense, consider the following. When you created the array, your array members and respective UUIDs looked like this:

/dev/sda1 = 1234567890
/dev/sdb1 = 0987654321
/dev/sdc1 = 1029384756

And the array was created as `mdadm --create /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1`

If, after a reboot, your array members now look like this:
/dev/sda1 = 0987654321
/dev/sdb1 = 1029384756
/dev/sdc1 = 1234567890

Then you need to reassemble the array as `mdadm --assemble /dev/md0 /dev/sdc1 /dev/sda1 /dev/sdb1` to maintain integrity.

You might also try booting off a liveCD like [SysRescueCD]("http://www.sysresccd.org/Main_Page"), which will do its best to assemble arrays which were declared with FD type partitions (which you did). The SysRescueCD is an amazingly robust liveCD based on Gentoo which has gotten me out of numerous pickles, and also allowed me to do horrible things to my computer (e.g. migrate to a BTRFS root partition).

---

### Post by valuntahr on 2010-01-28
Now I did make a bunch of changes to the order of the drives in the BIOS when I was trying to fix some other issues, and I don't remember what the original order was. 

So, using sysrescuecd i would just need to run mdadm --assemble --scan again? or is there another method to recreate the arrays?

---

### Post by falconindy on 2010-01-28
Highly likely the changes you made in the BIOS are the cause of the array failure. Brute force it -- with only 3 drives in the array there's only 6 possible sequences. Entering the wrong sequence isn't going to make your cat explode.

If you still want to try the SysRescueCD route, it'll automatically try to start the array on boot. Not sure of the method(s) it uses.

---

### Post by falconindy on 2010-01-28
Highly likely the changes you made in the BIOS are the cause of the array failure. Brute force it -- with only 3 drives in the array there's only 6 possible sequences. Entering the wrong sequence isn't going to make your cat explode.

If you still want to try the SysRescueCD route, it'll automatically try to start the array on boot. Not sure of the method(s) it uses.

---

### Post by valuntahr on 2010-01-28
Finally solved the problem. One problem was the fact that my mdadm.conf file was completely empty except for the MAILADDR line, which was fixed by copying the basic mdadm.conf file from the System Rescue CD. 

The problem of actually creating the arrays again was solved by running the assembly command again and specifying the partition information, which I had omitted the first time through.

Thanks for your help.

---

