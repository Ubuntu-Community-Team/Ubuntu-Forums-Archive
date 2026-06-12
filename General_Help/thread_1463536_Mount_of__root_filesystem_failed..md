---
title: "Mount of  root filesystem failed."
date: 2010-04-27
forum: General Help
---

### Post by idesperado on 2010-04-27
Good evening to everyone!
First, I want to say : "Sorry for my bad English".
A have a problem with boot of system. ( 9.10 updated yesterday )
Problem came out after using Mount Manager.
That`s what I see on screen 
> 
Mount of  root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.

After using Ctrl+D there is a message on screen before reboot:
>  umont proc/sys/fs/binfmt_misc not mounted
        umount /dev  device is busy
          
        (In some cases useful info about process that use the device is found by isof (8) or fuser(1))

this message appears just for 1 second, after that computer going to reboot. That`s why I`m not sure that I`ve given text of this exactly.
Hope you can help me.
One more sorry for my bad English,
Thx.

---

### Post by john newbuntu on 2010-04-27
Welcome to the forums.  We'll try to fix it for ya.

How is your partition layout and which partition has the linux root filesystem? You can boot from a liveCD,  run "sudo fdisk -l" at the terminal(application->accessories->terminal) and post the output.

---

### Post by Nisal on 2010-04-27
well i got same **** twice also and this is my results any permanent solution for that 

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaeccaecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             757        4864    32997510    f  W95 Ext'd (LBA)
/dev/sda3              27         756     5863725   83  Linux
/dev/sda5            1306        4864    28587636    7  HPFS/NTFS
/dev/sda6             757        1305     4409779+  82  Linux swap / Solaris

---

### Post by idesperado on 2010-04-27
> **john newbuntu said:**
> Welcome to the forums.  We'll try to fix it for ya.

How is your partition layout and which partition has the linux root filesystem? You can boot from a liveCD,  run "sudo fdisk -l" at the terminal(application->accessories->terminal) and post the output.
Thx. =) I`ve done this actions, and this is output :

```

root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5abd5ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14932   119941258+   7  HPFS/NTFS
/dev/sda2           14933       19457    36347062+   5  Extended
/dev/sda5   *       14933       19265    34804791   83  Linux
/dev/sda6           19266       19457     1542208+  82  Linux swap / Solaris

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x001f001e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    7  HPFS/NTFS


```

At HDD with Ubuntu I also have WIndows XP SP3

---

### Post by ibuclaw on 2010-04-27
> **Nisal said:**
> well i got same **** twice also and this is my results any permanent solution for that 

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaeccaecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             757        4864    32997510    f  W95 Ext'd (LBA)
/dev/sda3              27         756     5863725   83  Linux
/dev/sda5            1306        4864    28587636    7  HPFS/NTFS
/dev/sda6             757        1305     4409779+  82  Linux swap / Solaris

What version of Ubuntu?

And I presume you've done the usual fsck of the root filesystem.
When you go into maintenance mode, type in:
```
fsck /dev/sda1
```
And reboot by pressing **Ctrl+Alt+Del**

Regards

---

### Post by idesperado on 2010-04-27
I`ve done action 

```

fsck /dev/sd**

```
for all of my partitions

There is output:

```

root@ubuntu:~# fsck /dev/sda1
fsck from util-linux-ng 2.16
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
root@ubuntu:~# fsck /dev/sda2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
root@ubuntu:~# fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda5: recovering journal
/dev/sda5: clean, 165143/2179072 files, 1169526/8701197 blocks (check in 3 mounts)
root@ubuntu:~# fsck /dev/sda6
fsck from util-linux-ng 2.16
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda6
root@ubuntu:~# fsck /dev/sdb
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# fsck /dev/sdb1
fsck from util-linux-ng 2.16
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1
 
```


And it doesn`t helpes =((((

---

### Post by idesperado on 2010-04-27
Hey,dudes!!!
I solved this problem! =)))
 
And this is the way I`d fixed it, I`ll be happy, if my instruction eill help smb to ressurect his Ubuntu:
```
sudo -s
*Enter your password*
mkdir /mnt/ubuntu
mount /dev/sda5 /mnt/ubuntu
gedit /mnt/ubuntu/etc/fstab

```After performing this actions you`ll see text editor with your "broken" file in it
Don`t touch it now,continue to work with Terminal. Caution! Don`t forget to change /dev/sda5 in my code into name of your "broken" bootable partition.
```

cat /etc/fstab

```after performing this string you`ll see code of fstab file, whic was used 
by Ubuntu to start LiveCD session. Now paste it`s code to your "broken" file,
don`t forget to delete "broken" code. 
Save changes and reboot.
Profit! 
It works.
Sorry for my bad english. Please,edit my message if I was wrong.
Good luck!

---

### Post by john newbuntu on 2010-04-27
idesparado, glad that you solved the problem yourself.  However, please remember to NOT run fsck on mounted filesystems, swap and on ntfs partitions as well.  In your case, you could have run it from a liveCD.  Also make copies of files before changing them(such as /etc/fstab).

---

### Post by idesperado on 2010-04-27
Thx =)
Ubuntu rulezzz  =)
:guitar:

love this system and communitu of users.
Good luck! :)

---

