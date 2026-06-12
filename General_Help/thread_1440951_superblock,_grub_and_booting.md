---
title: "superblock, grub and booting"
date: 2010-03-28
forum: General Help
---

### Post by Infinitum_Omega on 2010-03-28
OK here goes..

I started using Ubuntu Hardy a while back, all was working well untill  Windows XP started giving problems, I re-installed XP ,not repairing but installing a second Windows folder on the ntfs partition(Not at all a good choice).So I rebooted and ,as I thought would happen, the grub loader wasn't loading, Just the old Windows loader. So I went to the Hardy Wiki and followed the instructions to restore grub(Using my live CD). I restored to MBR and partition. Then I tried booting and,sure enough, grub was loading so I selected Ubuntu and the splash appeared. I was now waiting at least a minute, nothing happening,I pressed Alt + Ctrl + F1, The after a while got this:

```
Starting up ...
Loading, please wait...
    Check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/XXXXXXXX-XXXX-XXXX-XXXXXXXXXXXX does not exist. Dropping to a shell!

BusyBox XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

(initramfs)
```So I went back to the live CD and saw that my ubuntu partition was unable to mount throwing this error : 

```
Cannot Mount volume
mount:/dev/sda2: can't read superblock
```I then went to terminal and entered the command : ```
mount -t ext2 /dev/sda2 /mnt
```It mounted and I could see all my files. So I tried running various e2fsck commands. 
When doing the e2fsck commands in ubuntu it constantly told me the drive was in use by something. Instead I used my PartImage CD to run these commands.
No errors were reported. I tried restoring the superblock but it made no difference. Now I'm completely stuck, I've read a load of pages on superblocks but none of the commands made a difference.

Are there any commands you can tell me about? Because I really don't want to revert to XP

```
The Drives:
/dev/sda1 - NTFS
/dev/sda2 - EXT2

```Chris

---

### Post by Infinitum_Omega on 2010-03-29
I fixed it lol! By firts deleting my current superblock the running e2fsck again. I'm on Ubuntu at this very moment!

Here's the guide(I'm posting it all, then summarizing my steps, I don't a dead link here in the future :p)

Linux EXT2/EXT3 Superblock Recovery

Each file system has one superblock, which contains information about file system such as file system type, size, status and information about other metadata structures. If it lost, you would be in trouble so Linux maintains multiple redundant copies of the superblock in every file system.

I read the article &#8220;Surviving a Linux Filesystem Failures&#8221; on nixCraft, and did the test that destroyed and also recovered the ext2 and ext3 filesystem superblock on Fedora 9. The following is the steps.

EXT2 filesystem

In my machine, there is an ext2 filesystem /dev/sda6 which its mount point is /fs2.

Firstly, I should know the location of superblocks and the size of block.
[root@localhost ~]# dumpe2fs /dev/sda6 | grep &#8211;i superblock
dumpe2fs 1.40.8 (13-Mar-2008)
  Primary superblock at 1, Group descriptors at 2-2
  Backup superblock at 8193, Group descriptors at 8194-8194
  Backup superblock at 24577, Group descriptors at 24578-24578
  Backup superblock at 40961, Group descriptors at 40962-40962
  Backup superblock at 57345, Group descriptors at 57346-57346
  Backup superblock at 73729, Group descriptors at 73730-73730
[root@localhost ~]# dumpe2fs /dev/sda6 | grep &#8211;i &#8216;block size&#8217;
dumpe2fs 1.40.8 (13-Mar-2008)
Block size:                               1024 

From the above, I knew there are 5 backup superblocks and the block size is 1024 bytes. The location of primary superblock is at 1. The locations of these 5 backup superblocks are at 8193,24577,40961,57345 and 73729 respectively. If you want to know the filesystem&#8217;s block size, there are another two ways that you can use tune2fs and ext3grep commands. For example,
[root@localhost ~]# tune2fs &#8211;l dev/sda6 | grep &#8211;i &#8216;block size&#8217;
[root@localhost ~]# ext3grep /dev/sda6 | grep &#8211;i &#8216;block size&#8217; 

Then, I destroyed the superblock as below.
[root@localhost ~]# dd if=/dev/zero count=1 bs=1024 seek=1 of=/dev/sda6 

I checked the effect, and found I still could change to /fs2 directory. I could still list its contents. But the system gave me error messages when I tried to create a file or copy files.
[root@localhost ~]# cd /fs2
[root@localhost ~]# ll
total 19
drwx&#8212;&#8212; 2 root root 12288 2009-06-25 08:57 lost+found
-rw-r&#8212;r&#8212;1 root root   135 2009-06-25 18:15 qaz
 &#8230; &#8230; 

[root@localhost fs2]#cp qaz wsx
cp: overwrite  `wsx&#8217;? y
cp: writing `wsx&#8217;: No space left on device
 [root@localhost fs2]#cp qaz edc
cp: cannot create regular file `edc&#8217;: Input/output error 

When I run the dumpe2fs command, it told me the superblock had been destroyed.
[root@localhost fs2]#dumpe2fs /dev/sda6
dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda6
Couldn&#8217;t find valid filesystem superblock. 

I recovered the superblock.
[root@localhost ~]# dd if=/dev/sda6 count=1 bs=1024 skip=8193 seek=1 of=/dev/sda5

After that, I checked if I can create and copy files. I found they worked. And the command dumpe2fs could display normally. 

EXT3 filesystem

In my machine, there is another ext3 filesystem /dev/sda5 which its mount point is /fs3.

Check the location of superblocks and the size of block.
[root@localhost ~]# dumpe2fs /dev/sda5 | grep &#8211;i superblock
dumpe2fs 1.40.8 (13-Mar-2008)
  Primary superblock at 0, Group descriptors at 1-1
  Backup superblock at 32768, Group descriptors at 32769-32769
  Backup superblock at 98304, Group descriptors at 98305-98305
  Backup superblock at 163840, Group descriptors at 163841-163841
  Backup superblock at 229376, Group descriptors at 229377-22937
[root@localhost ~]# dumpe2fs /dev/sda5 | grep &#8211;i &#8216;block size&#8217;
dumpe2fs 1.40.8 (13-Mar-2008)
Block size:                               4096 

From the above, I knew there are 4 backup superblocks and the block size is 4096 bytes. The location of primary superblock is at 0. The locations of these 4 backup superblocks are at 32768, 98304, 163840, and 229376.

Destroy the superblock.
[root@localhost ~]# dd if=/dev/zero count=1 bs=4096 seek=0 of=/dev/sda5 

I found I still can change to /fs3 directory. But when I listed its contents, there is nothing. I used dumpe2fs command to check, it told me the superblock has problem. Then I tried to recover the superblock like the above approach, however, it did not work. I restarted the system. The system displayed it unable to resolve the filesystem and could not boot up. I entered the maintenance mode and tried to recover using the method as below. It did not work.
(Repair filesystem) 1 # e2fsck &#8211;f &#8211;b 32768 /dev/sda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program? 

Then I used another method, after I reboot the system it worded.
(Repair filesystem) 2 # e2fsck &#8211;f  /dev/sda5
(Repair filesystem) 3 # reboot 

From the test, I realized that the information of the filesystem&#8217;s superblock is very important. We&#8217;d better backup it to the root because we can still read it through maintenance mode even if the system can not boot up normally. Don&#8217;t forget run the following command.
#dumpe2fs /dev/sda5 > /dumpe2fs-sda5

[http://kezhong.wordpress.com/2009/06/27/linux-ext2ext3-superblock-recovery/#comment-206]("http://kezhong.wordpress.com/2009/06/27/linux-ext2ext3-superblock-recovery/#comment-206")

Here's What I did:
From my PartImage II Disk's terminal:

```
dumpe2fs /dev/hda2 | grep &#8211;i superblock
```

Noted the superblocks positions on paper (32768,98304...)

```
dumpe2fs /dev/hda2 | grep &#8211;i &#8216;block size&#8217; 
```

Noted Blocksize (Mine was 4096)

**Deleted superblock**
```
dd if=/dev/zero count=1 bs=1024 seek=0 of=/dev/hda2
```
[B]Seek=position of first superblock
bs= Your own byte size/block size[/B]

```
e2fsck /dev/hda2
```
It replaced the superblock

Rebooted and the problem was fixed :)

I know I'm still a noob but I hope to grow .LOL

---

