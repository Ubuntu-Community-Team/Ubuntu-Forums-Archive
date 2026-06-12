---
title: "Ubuntu 9.10 Mounting error: mounting dev/disk...on root failed: Invalid argument"
date: 2010-03-23
forum: General Help
---

### Post by Peterace on 2010-03-23
Hi Everyone!

I am currently dual booting Windows 7 and Ubuntu 9.10 64 bit on a HP laptop.  
However for some reason when I woke up this morning the Linux partition 
failed to boot.  The computer can successfully get to the 
Grub 2 (1.97~beta) boot screen and from there it can successfully 
boot into Windows 7 along with the memory test program.  
However, none of the primary Ubuntu booting options nor the Ubuntu 
recovery mode boot options work and both yield the following error and
associated console output: (There are multiple Ubuntu boot options 2 per kernel)

//Begin Console output-------------------------------------------------

mount: mounting /dev/disk/by-uuid/a3c31122-6794-4fa6-a039-91d49dadfa8a on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a lit of built in commands.

(initramfs)

//End Console output---------------------------------------------------

What I have done so far:
I started searching through the Forums here and elsewhere on the web,
for some reason most parts of the console output above done yield many
results.  The thing that I did get a lot of hits for was some variation of

Target filesystem doesn't have /sbin/init.

As far as I can tell this means that that Ubuntu drive is missing a critical
file necessary for boot up.

Just to make sure that my machine was actually trying to get to the right partition
and not the windows partion, I proceeded to cd and ls around the drive and was unable
to find anything Windows related like the programs folder, I also could not find
any of my linux documents.

I also found a couple of postings linking to the Wubi site that suggested I remount
my linux partition under my windows drive.  But I don't think that applies to me
because I did not use wubi installer.

[http://ubuntuforums.org/showthread.php?t=1421829](http://ubuntuforums.org/showthread.php?t=1421829)

Other posts suggested I do a minimal reinstallation with a live disk.  I have not
done this because I am worried about overwriting my windows partition.

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-booting-problem-497057/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-booting-problem-497057/)

Finally I ran into a couple of posts suggesting that I edit the grub files at the
boot menu by hitting the 'e' key on the keyboard.  Unfortunately the directions to do
that were not given as the asker was using 'lilo'.

[http://ubuntuforums.org/showthread.php?t=611251](http://ubuntuforums.org/showthread.php?t=611251)

Any help would be appreciated,
Thanks,
Hubert (Peter) Pan

---

### Post by andrewthomas on 2010-03-23
Did you install from a live CD? If you have it you can reinstall grub2 from it. There is some useful information here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> SIMPLEST - Copy GRUB 2 Files from the LiveCD
This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods.

Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".
```
sudo fdisk -l
```
If the user isn't sure of the partition, look for one of the appropriate size or formatting.
Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.
Mount the partition containing the Ubuntu installation.
```
sudo mount /dev/sd''xY'' /mnt
```
Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot
Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.
```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```
Example: sudo grub-install --root-directory=/mnt/ /dev/sda
Reboot
Refresh the GRUB 2 menu with ```
sudo update-grub
```
If the user wishes to explore why the system failed, refer to Post-Restoration Commands section below
The above link also explains the commands to enter at the grub> prompt if you wish to explore that option

---

### Post by Peterace on 2010-03-23
Hi andrewthomas,

Thanks for the reply, I tried running the commands in your post but unfortunately I could not complete the Grub reinstall.  Posted below is the terminal output my machine gave me.

//[terminal output starts here]----------------------------------------------------------------
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb74ff5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30545   245241856    7  HPFS/NTFS
/dev/sda3           30546       45752   122150227+  83  Linux
/dev/sda4           45753       60801   120881092+   5  Extended
/dev/sda5           45753       60184   115925008+  83  Linux
/dev/sda6           60185       60801     4956021   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D2509F76509F6051" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FAD4A299D4A257A1" TYPE="ntfs" 
/dev/sda3: LABEL="linux" UUID="0696ec73-036f-47fc-93ca-d93cd2b93ebb" TYPE="ext2" 
/dev/sda5: UUID="a3c31122-6794-4fa6-a039-91d49dadfa8a" TYPE="ext4" 
/dev/sda6: UUID="ae9b2a19-4078-4a1d-a63b-8b460d8a94f0" TYPE="swap" 
ubuntu@ubuntu:~$ sudo mount /dev/sda3
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /mnt/boot
mount: can't find /mnt/boot in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda5
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: /dev/sda3 already mounted or /mnt busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sd3
grub-probe: error: Cannot stat `/dev/sd3'
Invalid device `/dev/sd3'.
Try ``grub-setup --help'' for more information.
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda3
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/boot
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/boot /dev/sda3
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$ 

//[terminal output ends  here]----------------------------------------------------------------

In summary, I tried reinstalling grub to all available Linux partitions, but none of the installations succeeded.

I also tried browsing into a couple of drives from the live CD using graphical file browser, and while I could get into most of them, I failed to get into one of them which yielded the following error popup:

[IMG]http://farm5.static.flickr.com/4047/4458083404_56da625c8a_m.jpg[/IMG] 

Bigger Version: [http://www.flickr.com/photos/48665732@N06/4458083404/](http://www.flickr.com/photos/48665732@N06/4458083404/)

Thanks!

---

### Post by andrewthomas on 2010-03-23
I think that you did some extra steps. Boot again from the Live CD.  And select try Ubuntu without installing.

Then ```
sudo mount /dev/sda5 /mnt
```
then ```
sudo grub-install --root-directory=/mnt /dev/sda
```
then ```
sudo update-grub
```
and reboot.

---

### Post by Peterace on 2010-03-23
Hi andrewthomas,

Thanks for the follow up, unfortunately I still was unable to mount/install grub on /dev/sda5.  Apparently its group descriptors are corrupted, since I have no idea what that means, I attached the terminal output below:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[   89.338799] HDA Intel 0000:00:10.1: setting latency timer to 64
[   90.944067] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input10
[   91.182539] lp: driver loaded but no devices found
[   92.380997] ppdev: user-space parallel port driver
[   97.328907] usplash:395 freeing invalid memtype ffffffffd0000000-ffffffffd8000000
[  163.500041] Clocksource tsc unstable (delta = -243222906 ns)
[  187.118859] EXT4-fs (sda5): ext4_check_descriptors: Checksum for group 6 failed (31747!=58)
[  187.118879] EXT4-fs (sda5): group descriptors corrupted!
[  282.728198] EXT4-fs (sda5): ext4_check_descriptors: Checksum for group 6 failed (31747!=58)
[  282.728215] EXT4-fs (sda5): group descriptors corrupted!
ubuntu@ubuntu:~$ 

```Thanks!

---

### Post by andrewthomas on 2010-03-23
Boot back into the live CD and run fsck in the terminal WITHOUT mounting any partitions.
```
sudo fsck /dev/sda5
```

and post the output

---

### Post by Peterace on 2010-03-23
Hi andrewthomas,

Actually after I posted my last message I did a google search, and found and ran the fsck program before I checked the forum again for a reply.  (After starting the process I got cold feet, and aborted it).  Then I saw your reply, and ran it again.  The only issue is the first time, I ran it, it informed me that it fixed a lot of bits at the beginning of the  sector, and I have not been able to recreate that message.  As far as I can tell, it's starting off slightly before where I left off.  Hopefully that does not cause any issues.
```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
One or more block group descriptor checksums are invalid.  Fix<y>? yes

Group descriptor 83 checksum is invalid.  FIXED.
Group descriptor 84 checksum is invalid.  FIXED.
Group descriptor 93 checksum is invalid.  FIXED.
Group descriptor 94 checksum is invalid.  FIXED.
Group descriptor 95 checksum is invalid.  FIXED.
Group descriptor 96 checksum is invalid.  FIXED.
Group descriptor 97 checksum is invalid.  FIXED.
Group descriptor 98 checksum is invalid.  FIXED.
Group descriptor 99 checksum is invalid.  FIXED.
Group descriptor 100 checksum is invalid.  FIXED.
Group descriptor 101 checksum is invalid.  FIXED.
Group descriptor 102 checksum is invalid.  FIXED.
Group descriptor 103 checksum is invalid.  FIXED.
Group descriptor 104 checksum is invalid.  FIXED.
Group descriptor 105 checksum is invalid.  FIXED.
Group descriptor 106 checksum is invalid.  FIXED.
Group descriptor 107 checksum is invalid.  FIXED.
Group descriptor 108 checksum is invalid.  FIXED.
Group descriptor 109 checksum is invalid.  FIXED.
Group descriptor 110 checksum is invalid.  FIXED.
Group descriptor 111 checksum is invalid.  FIXED.
Group descriptor 112 checksum is invalid.  FIXED.
Group descriptor 113 checksum is invalid.  FIXED.
Group descriptor 114 checksum is invalid.  FIXED.
Group descriptor 115 checksum is invalid.  FIXED.
Group descriptor 116 checksum is invalid.  FIXED.
Group descriptor 117 checksum is invalid.  FIXED.
Group descriptor 118 checksum is invalid.  FIXED.
Group descriptor 119 checksum is invalid.  FIXED.
Group descriptor 120 checksum is invalid.  FIXED.
Group descriptor 121 checksum is invalid.  FIXED.
Group descriptor 122 checksum is invalid.  FIXED.
Group descriptor 123 checksum is invalid.  FIXED.
Group descriptor 124 checksum is invalid.  FIXED.
Group descriptor 125 checksum is invalid.  FIXED.
Group descriptor 126 checksum is invalid.  FIXED.
Group descriptor 127 checksum is invalid.  FIXED.
Group descriptor 129 checksum is invalid.  FIXED.
Group descriptor 130 checksum is invalid.  FIXED.
Group descriptor 131 checksum is invalid.  FIXED.
Group descriptor 132 checksum is invalid.  FIXED.
Group descriptor 133 checksum is invalid.  FIXED.
Group descriptor 134 checksum is invalid.  FIXED.
Group descriptor 135 checksum is invalid.  FIXED.
Group descriptor 136 checksum is invalid.  FIXED.
Group descriptor 137 checksum is invalid.  FIXED.
Group descriptor 138 checksum is invalid.  FIXED.
Group descriptor 139 checksum is invalid.  FIXED.
Group descriptor 140 checksum is invalid.  FIXED.
Group descriptor 141 checksum is invalid.  FIXED.
Group descriptor 142 checksum is invalid.  FIXED.
Group descriptor 143 checksum is invalid.  FIXED.
Group descriptor 145 checksum is invalid.  FIXED.
Group descriptor 146 checksum is invalid.  FIXED.
Group descriptor 147 checksum is invalid.  FIXED.
Group descriptor 148 checksum is invalid.  FIXED.
Group descriptor 149 checksum is invalid.  FIXED.
Group descriptor 150 checksum is invalid.  FIXED.
Group descriptor 151 checksum is invalid.  FIXED.
Group descriptor 152 checksum is invalid.  FIXED.
Group descriptor 153 checksum is invalid.  FIXED.
Group descriptor 154 checksum is invalid.  FIXED.
Group descriptor 155 checksum is invalid.  FIXED.
Group descriptor 156 checksum is invalid.  FIXED.
Group descriptor 157 checksum is invalid.  FIXED.
Group descriptor 158 checksum is invalid.  FIXED.
Group descriptor 159 checksum is invalid.  FIXED.
Group descriptor 161 checksum is invalid.  FIXED.
Group descriptor 162 checksum is invalid.  FIXED.
Group descriptor 163 checksum is invalid.  FIXED.
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Missing '..' in directory inode 274915.
Fix<y>? 


```Am I correct in guessing that I should be answering 'yes' to most of program prompts?

Thanks!

---

### Post by andrewthomas on 2010-03-23
> **Peterace said:**
> Am I correct in guessing that I should be answering 'yes' to most of program prompts?

Thanks!Yes you are correct.

---

### Post by Peterace on 2010-03-23
Hi andrewthomas,

Is it normal to have to reply 'y' for yes more than ~500 times?  So far I have been just holding down the 'y' key and watching the lines of output fly by.

Thanks!

---

### Post by andrewthomas on 2010-03-23
How is it going?  Is it all good now?

---

### Post by Peterace on 2010-03-23
Hi andrewthomas,

I just finished running the fsck program, and unfortunately it did not fix much.  When I try to start Ubuntu normally it just freezes on boot (I am guessing it kernel panicked because the caps lock key was flashing), and when I boot in recovery mode App Armor fails because it's profiles failed to load.

Since I really did not have anything important on my ubuntu partition that is not already replicated on my Windows partition I was planning on just reinstalling.  Unless of course, I find a solution that I missed earlier on line.  But given that the majority of my ubuntu operating system is sitting in the lost and found folder, I doubt it :).

Thanks for your help!:D

---

### Post by andrewthomas on 2010-03-23
You are welcome.

---

### Post by hiteshhp on 2012-02-13
> **andrewthomas said:**
> Did you install from a live CD? If you have it you can reinstall grub2 from it. There is some useful information here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The above link also explains the commands to enter at the grub> prompt if you wish to explore that option

Thanks andrewthomas

I had similar problem with ubuntu 11.04 and you saved me reinstallation.
Really great guy you are.

I followed three commands and it worked like a charm

Thanks a lot.

---

### Post by oldos2er on 2012-02-14
Closed, necromancy.

---

