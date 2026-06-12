---
title: "Was trying to access Windows files on my HD"
date: 2012-05-10
forum: General Help
---

### Post by JoeGoff on 2012-05-10
So i typed in the terminal "sudo apt-get install ntfs-3g" and i get this

"sudo: unable to open /var/lib/sudo/meg/2: Read-only file system"

Did i break something? Im fairly new to using linux and havent had any problems for a couple months, but now i cant do anything and i dont remember changing permissions.

helpsies please

---

### Post by oldfred on 2012-05-10
Welcome to the forums.

Is this a standard install or wubi?

You should not need to install the ntfs-3g as it is installed by default.

If standard install. Wubi has different instructions.
Did you reboot and have system issues. If a system issue it mounts everything read-only.

If you are having issues then you may need to run e2fsck.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s), sda1, sda5 or whatever it is.

#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by JoeGoff on 2012-05-10
i do apologize because i am a noob to all this linux terminology and actions, im so used to windows. 
this is an install of the 11 version off an ISO file and have been learning on my own, google and forums. 
so i opened a terminal and typed in e2fsck this is what i get

"Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list"

i have no idea what to do from here

---

### Post by oldfred on 2012-05-10
post this so I can give exact command. If you have more than one ext4 formated partition, explain which is which or / (root), /home, data etc.

```
sudo fdisk -lu
```

---

### Post by JoeGoff on 2012-05-10
sudo fdisk -lu
[sudo] password for meg: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bd3d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376   83  Linux

---

### Post by Owl94 on 2012-05-10
There's a simple program Gigolo (installed or in software center) which lets you access Windows drives using your file manager.

---

### Post by oldfred on 2012-05-10
From liveCD.

#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1           

But you only show one partition sda1 formated Linux. There is no NTFS formated partition for Windows.

Did you install and use the option to install to entire drive that clearly says it will overwrite all data?

Because Linux is smaller than Windows, if you did not backup before installing, you may be able to recover some data, but immediately stop using drive. You need another drive of nearly the same size to copy data to and it is a long process. Recovery software looks for anything that looks like a file and copies it. You do not have file names, just extensions and it recovers partial or previously delete files as well. It can be a long process to sort thru data.

---

### Post by JoeGoff on 2012-05-10
ty owl.

but how do i fix the read only problem i have?

---

### Post by JoeGoff on 2012-05-10
@oldfred

i bet you when i did install Ubuntu i more than likely partitioned the whole HD for Ubuntu. so ty for answering quickly to ease my mind
should i make a new post about the read only problem?

---

### Post by oldfred on 2012-05-10
If you have nothing to recover, then run the e2fsck commands on your sda1 partition. 
Ubuntu will usually come up in read only if there is a file issue that often fsck fixes.

---

### Post by JoeGoff on 2012-05-10
AHHHHHHHHHHHHHHHHHHHHHHH no way!!


meg@meg-HP-Pavilion-dv4-Notebook-PC:~$ fsck
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda1 is mounted.  


WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>?

---

### Post by oldfred on 2012-05-10
From post #7

[COLOR=DarkRed]From liveCD[/COLOR]. Otherwise you may damage system.

#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

