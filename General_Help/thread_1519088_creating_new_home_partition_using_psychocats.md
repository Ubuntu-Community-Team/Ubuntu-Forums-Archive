---
title: "creating new /home partition using psychocats"
date: 2010-06-27
forum: General Help
---

### Post by medphys on 2010-06-27
Hi all,

Ran into a roadblock in trying to create a new /home partition on my hard drive.  Used Gparted to create the new partition,when I mount the new partitions and checking to see if they are mounted I see that they are.  I then cd /old/home and then I use the command (find . -print0 | cpio --null --sparse -pvd /new/).  I get the following on all of my files:

cpio: cannot make directory `/new//./dan': Permission denied
cpio: /new//./dan/Music/Patsy Cline: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./dan': Permission denied
cpio: /new//./dan/Music/Louis Armstrong Orchestra/The Best Of Ken Burns Jazz/01 - Star Dust.mp3: Cannot open: No such file or directory
cpio: cannot make directory `/new//./dan': Permission denied
cpio: 

How can I clear the permission denied and copy my files to /new?

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42c742c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4197    33712371   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3            4198        9327    41206725   83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order



Thanks,

---

### Post by oldfred on 2010-06-28
I think it was this link that said cpio was not preferred anymore.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I followed psychocats but from some other sites used the cp command. With the cp command you have to use cp -a or cp -ax to preserve permissions.

---

### Post by dcstar on 2010-06-28
> **medphys said:**
> Hi all,

Ran into a roadblock in trying to create a new /home partition on my hard drive.  Used Gparted to create the new partition,when I mount the new partitions and checking to see if they are mounted I see that they are.  I then cd /old/home and then I use the command (find . -print0 | cpio --null --sparse -pvd /new/).  I get the following on all of my files:

cpio: cannot make directory `/new//./dan': Permission denied
cpio: /new//./dan/Music/Patsy Cline: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./dan': Permission denied
cpio: /new//./dan/Music/Louis Armstrong Orchestra/The Best Of Ken Burns Jazz/01 - Star Dust.mp3: Cannot open: No such file or directory
cpio: cannot make directory `/new//./dan': Permission denied
cpio: 

How can I clear the permission denied and copy my files to /new?
........

Make /new with permissions that allow you to use it:

```
sudo chown /new your-user-name
```

This should have been clearly stated in whatever instructions you used.

---

### Post by nothingspecial on 2010-06-28
You need a sudo just before the cpio bit.

It does mention that in the tutorial a few lines later I think
```

find . -print0 | sudo cpio --null --sparse -pvd /new/
```

---

