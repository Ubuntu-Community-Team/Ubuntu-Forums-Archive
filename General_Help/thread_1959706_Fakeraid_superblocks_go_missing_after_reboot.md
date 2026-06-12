---
title: "Fakeraid superblocks go missing after reboot"
date: 2012-04-16
forum: General Help
---

### Post by stochastic79 on 2012-04-16
I have searched these forums and Google and none of the leads go anywhere although [_this post_]("http://ubuntuforums.org/showthread.php?t=1785888") is pretty close match for the problem I describe below. However, rather than revive a 10 month old thread, I will start afresh with my particular circumstances:

I have a 6TB RAID5 built onboard through the H67 chipset. I installed XBMCbuntu onto a separate, i.e. non-member, 250GB drive. During installation I formatted the array using the installer's partition editor. The drive seemed fine and I went about setting up the system. However, after reboot it had disappeared and I thought perhaps I had forgotten something or done something wrong during the installation.

Although this was a bit odd, it did not alarm me too much because I could see that /dev/mapper/isw_bcgafdbfhb_Media still existed. I was able to reformat this (as ext4) and then mount the array successfully.

I then proceeded to transfer about 4TB of data and life was happy for a few weeks until I needed to restart the machine.

During boot the system complained that the drive (i.e. array) was not ready. So I skipped mounting it, let the system boot up and the and went in to investigate...

Trying a regular mount gave an unhelpful error:
```
dave@XBMC:~$ sudo mount -t ext4 /dev/mapper/isw_bcgafdbfhb_Media1 /mnt/media
mount: special device /dev/mapper/isw_bcgafdbfhb_Media1 does not exist
```

Checking the device with fdisk made it complain about GPT so I used gdisk to check that the partition was still there:

```
dave@XBMC:~$ sudo gdisk -l /dev/mapper/isw_bcgafdbfhb_Media
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/mapper/isw_bcgafdbfhb_Media: 11721073920 sectors, 5.5 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8B4AEA2E-7CE0-4AA6-922A-C275D588124A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 11721073886
Partitions will be aligned on 2048-sector boundaries
Total free space is 3261 sectors (1.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048     11721072639   5.5 TiB     0700

```

Ok, now I look with parted, which reports an ext4 filesystem:

```
dave@XBMC:~$ sudo parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) select /dev/mapper/isw_bcgafdbfhb_Media
Using /dev/mapper/isw_bcgafdbfhb_Media
(parted) print
Model: Linux device-mapper (raid45) (dm)
Disk /dev/mapper/isw_bcgafdbfhb_Media: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6001GB  6001GB  ext4

(parted) q
dave@XBMC:~$
```

I check the filesystem with fsck and hit the first clue:

```
dave@XBMC:~$ sudo fsck.ext4 -v /dev/mapper/isw_bcgafdbfhb_Media
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/mapper/isw_bcgafdbfhb_Media

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

(sidenote: why does the last part talk about ext2?)

Anyway, it looks like a superblock problem so I try to recover from a backup superblock.

First list the backup locations:

```
dave@XBMC:~$ sudo mke2fs -n /dev/mapper/isw_bcgafdbfhb_Media
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
366288896 inodes, 1465134240 blocks
73256712 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
44713 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544
dave@XBMC:~$

```

Then restore from one of those locations:
```

dave@XBMC:~$ sudo e2fsck -b 32768 /dev/mapper/isw_bcgafdbfhb_Media
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/mapper/isw_bcgafdbfhb_Media

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

dave@XBMC:~$

```

I get the same bad magic number for any of the backup superblocks. I also get the bad magic number error for dumpe2fs.

I am hesistant to reformat and reboot just to verify the 'vanishing superblocks' problem that is mentioned in [_that other post_]("http://ubuntuforums.org/showthread.php?t=1785888"). Does anyone have any ideas how I can get this mounted or at least recover some data? The data was nothing irreplaceable but it's annoying to think that it might have vanished. I might be less annoyed too if I can work out how this problem occurred.

Any help from the Ubuntu Community would be very much appreciated!

---

### Post by stochastic79 on 2012-04-17
Hmmm ... I was back in gparted and noticed that the raid flag was not set for the partition. When I checked the raid flag the drive became mountable again.

This new clue led me to this thread: [http://ubuntuforums.org/showthread.php?p=11741146](http://ubuntuforums.org/showthread.php?p=11741146)

I was already running the latest version of dmraid, sourced from the regular Ubuntu repositories but I will try adding Phillip Susi's Personal Package Archive to my system and see if it fixes the problem over a reboot.

---

