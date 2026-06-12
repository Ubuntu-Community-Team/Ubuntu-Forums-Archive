---
title: "ext4 file system hosed after Ubuntu 11 upgrade (duplicate directory &amp; file names)"
date: 2011-05-08
forum: General Help
---

### Post by Moorlock on 2011-05-08
I recently upgraded to **Ubuntu 11** and a few days later my **ecryptfs** filesystem began misbehaving in a weird way.

In my home directory, many subdirectory names are duplicated verbatim.  Here's an [FONT="Courier New"]ls -F[/FONT] excerpt:
[FONT="Courier New"]...
Desktop/
Desktop/
Documents/
Documents/
Downloads/
Downloads/
...[/FONT]
I can no longer access files in those directories (if I [FONT="Courier New"]ls[/FONT] the directory, it appears empty; I can [FONT="Courier New"]cd[/FONT] to it, but there's nothing inside).

Not all of the directories are duplicated/damaged like this, but most are.  A few non-directory files are also duplicated in this fashion, so for example:
[FONT="Courier New"]-rw-r--r--1 dgross dgross 95 2011-05-08 16:16 .dmrc
-rw-r--r--1 dgross dgross 95 2011-05-08 16:16 .dmrc[/FONT]
But I can read the contents of those files.

Because of the empty/damaged directories I can only start up in crippled recovery mode (too many essential files are impossible to find).  Also many important content files are missing and I'd love to be able to recover them.

The file system info is
/dev/sda1 [ext4]
(there's also an sda5 / swap)
ATA WDC WD5000BEVT-6
574ddb2a-84ea-43bc-9f1e-78256acf8bb2

I haven't had any luck doing anything useful with gparted, fstab, or fsck.  (I was able to force an fsck full scan at reboot, but it didn't complain of any problems.)

I would appreciate any help you could give me in diagnosing and fixing this problem.  Please let me know what additional information you need and (if you can) a hint on how to gather it, as I'm only somewhat linux savvy.

---

### Post by Moorlock on 2011-05-08
[FONT="Courier New"]> **sudo fsck.ext4 /dev/sda1 -f -v**
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  250236 inodes used (0.84%)
    5514 non-contiguous files (2.2%)
     559 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 216180/243
23781951 blocks used (19.98%)
       0 bad blocks
       1 large file
  181532 regular files
   26200 directories
      59 character device files
      26 block device files
       0 fifos
     423 links
   42407 symbolic links (33715 fast symbolic links)
       3 sockets
--------
  250650 files[/FONT]

---

### Post by Moorlock on 2011-05-08
This looks like a possibly useful datapoint:

[FONT="Courier New"]> **dmesg | grep ryptfs**
[  782.510299] Mount on filesystem of type eCryptfs explicitly disallowed due to known incompatibilities[/FONT]

---

### Post by Moorlock on 2011-05-09
I just went into [FONT="Courier New"]...home/.ecryptfs/*myname*[/FONT] and did an [FONT="Courier New"]ls -laF .Private/[/FONT] and was surprised to see both encrypted and unencrypted names of the duplicated files and directories!

e.g.
...
[FONT="Courier New"]drwxr-xr-x  2 1000 1000 4096 2011-05-07 05:12 Downloads/
drwxr-xr-x 22 1000 1000 4096 2011-05-05 03:11 ECRYPTFS_FNEK_ENCRYPTED.Gobbledygook--/[/FONT]
...

I'm not familiar enough with ecryptfs to know for sure, but that doesn't smell right to me. I think I'm going to try to move the unencrypted versions off to somewhere else and then remount the directory to see if that fixes things.

---

### Post by matt_symes on 2011-05-09
Hi

I have no idea what the problem may be but please keep posting your investigations.

Kind regards

---

### Post by Moorlock on 2011-05-09
I moved all of the unencrypted files & directories out of .Private/ and rebooted.  My home directory mounted as it ought to (though somewhat slowly... not sure what that's about) and at first glance it seems like everything is where it ought to be.  Hope this helps the next poor sucker who runs into this.

---

