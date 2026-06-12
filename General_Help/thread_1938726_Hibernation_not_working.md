---
title: "Hibernation not working"
date: 2012-03-10
forum: General Help
---

### Post by astrobob.tk on 2012-03-10
Hello,

A few months ago, hibernation & suspend stopped working on my laptop.

A while ago before this happens, I got the error (see attached image) which happenned "after" startup from a hibernation stat. I did the following:

```
$ sudo fsck /dev/sda7
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda7: recovering journal
/dev/sda7 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda7: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda7: 543684/1525920 files (0.2% non-contiguous), 3383313/6103296 blocks

```After a few days:

```
dmesg:

[ 5183.888957] usb 3-1.3: USB disconnect, address 20
[ 5183.889367] btusb_send_frame: hci0 urb ea6d9800 submission failed
[ 5199.014094] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-22]
[ 5199.014100] ecryptfs_create: Failed to create file inlower filesystem
[ 5207.277155] EXT4-fs error (device sda8): ext4_free_inode: bit already cleared for inode 2099738
[ 5207.488216] EXT4-fs error (device sda8): ext4_free_inode: bit already cleared for inode 2099728
[ 5209.732688] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378148(bit 23460 in group 316)
[ 5209.732696] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378149(bit 23461 in group 316)
[ 5209.732700] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378150(bit 23462 in group 316)
[ 5209.732704] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378151(bit 23463 in group 316)
[ 5209.732708] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378152(bit 23464 in group 316)
[ 5209.732711] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378153(bit 23465 in group 316)
[ 5209.732715] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378154(bit 23466 in group 316)
[ 5209.732719] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378155(bit 23467 in group 316)
[ 5209.732722] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378156(bit 23468 in group 316)
[ 5209.732726] EXT4-fs error (device sda8): mb_free_blocks: double-free of inode 0's block 10378157(bit 23469 in group 316)
[ 5210.103102] JBD: Spotted dirty metadata buffer (dev = sda8, blocknr = 0). There's a risk of filesystem corruption in case of system crash.
[ 5234.084241] EXT4-fs error (device sda8): ext4_mb_generate_buddy: EXT4-fs: group 315: 22675 blocks in bitmap, 22665 in gd
[ 5234.084256] JBD: Spotted dirty metadata buffer (dev = sda8, blocknr = 0). There's a risk of filesystem corruption in case of system crash.
[ 5234.084335] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-22]
[ 5234.084337] ecryptfs_create: Failed to create file inlower filesystem
[ 5234.135908] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-22]
[ 5234.135918] ecryptfs_create: Failed to create file inlower filesystem
[ 5234.157267] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-22]
[ 5234.157271] ecryptfs_create: Failed to create file inlower filesystem
[ 5234.163088] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-22]
[ 5234.163097] ecryptfs_create: Failed to create file inlower filesystem
[ 5269.495931] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-22]
[ 5269.495941] ecryptfs_create: Failed to create file inlower filesystem

``````
$ sudo fsck /dev/sda7
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda7: recovering journal
Clearing orphaned inode 261145 (uid=1000, gid=1000, mode=0100600, size=3811)
Clearing orphaned inode 261144 (uid=1000, gid=1000, mode=0100600, size=2015)
Clearing orphaned inode 261143 (uid=1000, gid=1000, mode=0100600, size=6697)
Clearing orphaned inode 261142 (uid=1000, gid=1000, mode=0100600, size=4332)
Clearing orphaned inode 261141 (uid=1000, gid=1000, mode=0100600, size=6680)
Clearing orphaned inode 261140 (uid=1000, gid=1000, mode=0100600, size=40760)
Clearing orphaned inode 261139 (uid=1000, gid=1000, mode=0100600, size=14012)
Clearing orphaned inode 261138 (uid=1000, gid=1000, mode=0100600, size=56500)
Clearing orphaned inode 261136 (uid=1000, gid=1000, mode=0100600, size=42732)
Clearing orphaned inode 261135 (uid=1000, gid=1000, mode=0100600, size=2428)
Clearing orphaned inode 261134 (uid=1000, gid=1000, mode=0100600, size=726)
Clearing orphaned inode 261133 (uid=1000, gid=1000, mode=0100600, size=7314)
Clearing orphaned inode 261132 (uid=1000, gid=1000, mode=0100600, size=2085)
Clearing orphaned inode 261131 (uid=1000, gid=1000, mode=0100600, size=2973)
Clearing orphaned inode 261130 (uid=1000, gid=1000, mode=0100600, size=2645)
Clearing orphaned inode 261129 (uid=1000, gid=1000, mode=0100600, size=270)
/dev/sda7: clean, 543661/1525920 files, 3303193/6103296 blocks


after reboot:

$ sudo fsck /dev/sda7
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda7: recovering journal
Clearing orphaned inode 261145 (uid=1000, gid=1000, mode=0100600, size=3811)
Clearing orphaned inode 261144 (uid=1000, gid=1000, mode=0100600, size=2015)
Clearing orphaned inode 261143 (uid=1000, gid=1000, mode=0100600, size=6697)
Clearing orphaned inode 261142 (uid=1000, gid=1000, mode=0100600, size=4332)
Clearing orphaned inode 261141 (uid=1000, gid=1000, mode=0100600, size=6680)
Clearing orphaned inode 261140 (uid=1000, gid=1000, mode=0100600, size=40760)
Clearing orphaned inode 261139 (uid=1000, gid=1000, mode=0100600, size=14012)
Clearing orphaned inode 261138 (uid=1000, gid=1000, mode=0100600, size=56500)
Clearing orphaned inode 261136 (uid=1000, gid=1000, mode=0100600, size=42732)
Illegal inode 1318790724 in orphaned inode list.
/dev/sda7 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(1081368--1081369) -(1082828--1082838) -1082840 -(1082842--1082843) -1082950 -1082961 -1082985
Fix<y>? yes

Free blocks count wrong for group #33 (987, counted=1006).
Fix<y>? yes

Free blocks count wrong (2800054, counted=2800073).
Fix<y>? yes

Free inodes count wrong for group #32 (243, counted=251).
Fix<y>? yes

Free inodes count wrong (982249, counted=982257).
Fix<y>? yes


/dev/sda7: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda7: 543663/1525920 files (0.2% non-contiguous), 3303223/6103296 blocks


```The problem lies in:

1) At login, one of the cpu's is being used mostly by the gnome-system-daemon & the system is in a state in which I cannot work with for 5~7 minutes. I have a thread on this here: [http://ubuntuforums.org/showthread.php?t=1938720](http://ubuntuforums.org/showthread.php?t=1938720)

2)  Every time I login, anything I start freezes hang  & so does the volume control (i can't control them from the touch  controls above the keyboard) until a few minutes.

3) Hibernation & suspend do not work any more.

P.S.: for a few months, I was on WIFI only & all updates were done on wifi. is this related?

Can you please help? thanks

---

### Post by astrobob.tk on 2012-03-14
bump

---

