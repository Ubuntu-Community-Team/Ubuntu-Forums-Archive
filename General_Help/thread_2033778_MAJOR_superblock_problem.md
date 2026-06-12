---
title: "MAJOR superblock problem"
date: 2012-07-26
forum: General Help
---

### Post by dennis1200 on 2012-07-26
I have a hosed superblock as a result of a power outage and I cannot manage to repair it. I've followed the steps to restore a superblock from backup as described here: [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/]("https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/") but to no avail. The error I now get when trying to run fsck is ```
"No such device or address while trying to open /dev/sda1. Possibly non-existent or swap device?"
```
or also sometimes ```
Error writing block 32768 (Attempt to write block to filesystem resulted in short write).
```. Also can't figure out why sometimes I get one, sometimes the other. 32768 and all the other superblock backup numbers show up in that last error.

I can't boot into Ubuntu or a separate Windows partition. fdisk and parted see the partitions clearly, types and all, but no boot, no mount, and I've got a lot of data I need to at least transfer elsewhere. Dumpe2fs or mke2fs clearly list the superblock backups but they don't seem to help.

Any help is GREATLY appreciated - I've tried everything I've come across in the Google and ubuntuforums. I've tried mounting specifically with a backup superblock but that doesn't work either.

I can mount it manually with an fstab entry but no files appear; clicking on properties indicates that there are a couple hundred gigs of data but contents says "nothing".

---

### Post by dennis1200 on 2012-07-27
I suppose it goes without saying that I'd like to find a solution that doesn't involve me trying to rescue everything with testdisk/photorec and rewriting the entire hard drive.

---

### Post by oldfred on 2012-07-27
I have not had to repair, other than e2fsck.  think you have done what I have saved as a procedure. Someone also posted a last ditch procedure.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by dennis1200 on 2012-07-27
Those are all great links, and I appreciate you assembling them. Unfortunately, I can't seem to get any of them to work for me - but it seems so close! Here's a dump of the results of e2fsck, if that helps.

First- fdisk (sdh6 is the one I want to restore):
```
  Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048   200002047   100000000    7  HPFS/NTFS/exFAT
/dev/sdh2      1924849664  1953521663    14336000    7  HPFS/NTFS/exFAT
/dev/sdh4       200003582  1885786111   842891265    5  Extended
/dev/sdh5      1872115712  1885786111     6835200   82  Linux swap / Solaris
/dev/sdh6       200003584  1872115711   836056064   83  Linux

```

e2fsck ends with a message about an invalid journal inode and:
```
Recreate journal? yes                                                          

Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***

/dev/sdb6: ***** FILE SYSTEM WAS MODIFIED *****

  404189 inodes used (0.77%)
    1595 non-contiguous files (0.4%)
     524 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 350943/204
42386381 blocks used (20.28%)
       0 bad blocks
       2 large files

  298764 regular files
   37502 directories
      57 character device files
      25 block device files
       0 fifos
4294949587 links
   86045 symbolic links (71164 fast symbolic links)
      13 sockets
--------
  193830 files
Error writing block 32768 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 98304 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 163840 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 229376 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 294912 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 819200 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 884736 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 1605632 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 2654208 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 4096000 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 7962624 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 11239424 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 20480000 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 23887872 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 71663616 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 78675968 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

Error writing block 102400000 (Attempt to write block to filesystem resulted in short write).  Ignore error? yes

```
All those block errors are also the superblock backups, which might explain why I have a problem.

---

### Post by dennis1200 on 2012-07-27
I have also already tried clearing the journal inode with dumpe2fs and clri <8>

---

### Post by oldfred on 2012-07-27
You are beyond what I know.

The one user that it worked for,  did seem to have similar issue but I am not 100% sure of what combination of repairs ended up working for him.

---

### Post by dennis1200 on 2012-07-29
Do you think it may have something to do with the fact that Ubuntu is in an extended partition?

---

### Post by dennis1200 on 2012-07-29
In what remains something of a mystery, things now seems to be fixed. Every time I would run e2fsck, I'd get completely different error messages, everything from "zero-length partition" errors to wrong fs type errors to listing the number of files and directories appropriately and looking like it worked, but on a lark I did it one more time (20th time, about), specifying an alternate superblock (which I did many times before, seemingly to no avail), simply:
```
e2fsck -fyv -b 98304 /dev/sdh6
```
I haven't tried rebooting yet, but I mounted read-only successfully and am now copying everything to an external drive just in case. What seems puzzling to me is that I tried several other methods in the meantime which I thought would have prevented anything else from working (like formatting all the superblocks), but I'll take it.
Thanks for the help, oldfred.

---

### Post by oldfred on 2012-07-29
Any progress is good, glad you at least got data back, hope rebooting works.

---

### Post by dennis1200 on 2012-07-29
Final update - fully bootable, operational system. All data present and accounted for.

---

