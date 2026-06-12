---
title: "Shut down incorrectly; Ubuntu won't start"
date: 2010-11-21
forum: General Help
---

### Post by Jetro on 2010-11-21
This is kind of related to [this thread](http://ubuntuforums.org/showthread.php?t=1601810). Ubuntu refuses to start after my laptop lost power without a battery plugged in, meaning it immediately shut down whilst running (Ubuntu).

I get the same error message:
```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target Filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.
```
but it progresses differently from there.

Ubuntu is installed in sda**5**. It's not mounted or not even listed in "Places" when I boot from live USB.

Here is a bunch of commands I've run, enjoy.

*bunch of nonsense*

---

### Post by MooPi on 2010-11-21
Your not giving e2fsck any options. Try ```
e2fsck -p /dev/sda1
``` This will try to automatically repair. You should be doing this from the live CD or bootable usb.

---

### Post by Jetro on 2010-11-21
Oh, right.
```
sudo e2fsck -p /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
```

---

### Post by MooPi on 2010-11-21
Try the recommendation ```
e2fsck -b 8193 -p /dev/sda1
```

---

### Post by Jetro on 2010-11-21
```
sudo e2fsck -b 8193 -p /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
```
Wait, uh. I think I've gotten something wrong here. Seems Windows is running on sda1, and Ubuntu on sda5... it did not appear before. Damn it, sorry for wasting your time.

```
sudo e2fsck -p /dev/sda5
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```

```
sudo lsof /dev/sda5
lsof: WARNING: can't stat() tmpfs file system /cow
Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
Output information may be incomplete.
```

---

### Post by MooPi on 2010-11-21
Damm, okay try this. ```
mke2fs -n /dev/sda1
```
This should give you alternate superblock locations to check

Ignore last command then and unmount /dev/sda5 before attempting e2fsck.

---

### Post by Jetro on 2010-11-21
```
sudo mke2fs -n /dev/sda1
mke2fs 1.41.12 (17-May-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7815168 inodes, 31248425 blocks
1562421 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
954 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
4096000, 7962624, 11239424, 20480000, 23887872
```
Hm, now I'm kind of confused. It says the OS type is Linux? Yet GParted suggests it is Windows. It's even labeled as that, a label I gave it long ago, before any of this happened, and it is indeed Windows. Odd.

I did:
```
umount /dev/sda5
umount: /dev/sda5 is not mounted (according to mtab)
```

but I still get this message:
```
sudo e2fsck -p /dev/sda5
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```

Hmm. The last thing I did in Ubuntu, was writing a document. When I tried to open the document in Windows (from a ntfs drive that Windows and Ubuntu "shares"), I got a warning that it was in use by the username I use in Ubuntu. Is that of any help?

---

### Post by MooPi on 2010-11-21
Let's start from scratch.
```
sudo parted -l
```

---

### Post by Jetro on 2010-11-22
```
sudo parted -l
Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 128GB 128GB primary ntfs boot
3 128GB 150GB 21.5GB primary ntfs
2 150GB 160GB 10.5GB extended
5 150GB 160GB 10.0GB logical ext4
6 160GB 160GB 495MB logical linux-swap(v1)
```

---

### Post by MooPi on 2010-11-22
How are you checking the disks ? From a live CD, usb drive, ?

---

### Post by Jetro on 2010-11-22
> **MooPi said:**
> How are you checking the disks ? From a live CD, usb drive, ?
USB. There was a section for that, too, but I didn't include it.

---

### Post by MooPi on 2010-11-22
Okay I know we have covered this but humor me and attempt 
```
e2fsck -p /dev/sda2
```
Post back any errors.

---

### Post by Jetro on 2010-11-22
:p

```
sudo e2fsck -p /dev/sda2
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
```

---

### Post by MooPi on 2010-11-22
Okay just one more time
```
e2fsck -p /dev/sda5
```

---

### Post by Jetro on 2010-11-22
```
sudo e2fsck -p /dev/sda5
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

```

**Commands suggested in [_another thread_](http://ubuntuforums.org/showthread.php?t=744246)**:
```
sudo mke2fs -n /dev/sda5
mke2fs 1.41.12 (17-May-2010)
/dev/sda5 is apparently in use by the system; will not make a filesystem here!
```

```
dmesg | tail
[ 3213.512180] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[ 3213.512189] [drm] nouveau 0000:01:00.0: 0xC80C: Parsing digital output script table
[ 7755.356868] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 7755.356877] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[ 7755.356885] [drm] nouveau 0000:01:00.0: 0xC81B: Parsing digital output script table
[ 8404.340642] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[ 8404.340651] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[ 8404.340659] [drm] nouveau 0000:01:00.0: 0xC89F: Parsing digital output script table
[ 8404.512085] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[ 8404.512095] [drm] nouveau 0000:01:00.0: 0xC80C: Parsing digital output script table
```

```
sudo tune2fs -l /dev/sda5
tune2fs 1.41.12 (17-May-2010)
Filesystem volume name: <none>
Last mounted on: /
Filesystem UUID: aae24d75-1de1-4fd2-a5f4-20d3d11efee0
Filesystem magic number: 0xEF53
Filesystem revision #: 1 (dynamic)
Filesystem features: has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags: signed_directory_hash 
Default mount options: (none)
Filesystem state: clean with errors
Errors behavior: Continue
Filesystem OS type: Linux
Inode count: 612000
Block count: 2445896
Reserved block count: 122294
Free blocks: 137056
Free inodes: 371748
First block: 0
Block size: 4096
Fragment size: 4096
Reserved GDT blocks: 597
Blocks per group: 32768
Fragments per group: 32768
Inodes per group: 8160
Inode blocks per group: 510
RAID stride: 32603
Flex block group size: 16
Filesystem created: Mon Jul 19 22:51:25 2010
Last mount time: Wed Nov 17 14:55:09 2010
Last write time: Wed Nov 10 20:17:38 2010
Mount count: 11
Maximum mount count: 22
Last checked: Wed Nov 10 20:17:38 2010
Check interval: 15552000 (6 months)
Next check after: Mon May 9 20:17:38 2011
Lifetime writes: 165 GB
Reserved blocks uid: 0 (user root)
Reserved blocks gid: 0 (group root)
First inode: 11
Inode size:	 256
Required extra isize: 28
Desired extra isize: 28
Journal inode: 8
First orphan inode: 132625
Default directory hash: half_md4
Directory Hash Seed: aef37b51-6f4f-4077-814e-2423359a9a27
Journal backup: inode blocks
```

---

### Post by MooPi on 2010-11-22
We haven't tried this yet partition
```
sudo mke2fs -n /dev/sda2
```
Post results. I'm running out of options and really scratching my head on this. I'm hoping to get a result from mke2fs.

---

### Post by Jetro on 2010-11-22
Hehe, okay. I appreciate the help you have given me anyway.
Do you think my files in that Ubuntu partition are lost?

```
sudo mke2fs -n /dev/sda2
mke2fs 1.41.12 (17-May-2010)
mke2fs: inode_size (128) * inodes_count (0) too big for a
filesystem with 0 blocks, specify higher inode_ratio (-i)
or lower inode count (-N).
```

---

### Post by MooPi on 2010-11-22
You can't view the files while booting from usb drive ?  If you can see the files you can transfer to storage media, but you may have lost the install. All the threads from searches to research your problem end in lost bootable systems. The last bit of info would be try to use testdisk to recover lost data. Research  is all I've got on that because I've never had to use it.

---

### Post by Jetro on 2010-11-22
No, I can't view them from the USB drive. When I try to mount the disk I get an error (of course...):
```
Unable to mount 10 GB Filesystem
DBus error org.gtk.Private.Remote.VolumeMonitor.Failed: An Operation is already pending
```

I find it weird that sda2, the "extended" partition, is unchangeable from GParted because it says it's "busy (at least one logical partition is mounted).

---

### Post by MooPi on 2010-11-22
I may have a solution to your problem....
From Gparted disable the swap partition. It is part of your extended partition of 10.5 gig, and your usb drive may be using to function. I'm guessing but recollect this from another post.

---

### Post by Jetro on 2010-11-22
*Double post, my bad*

*Double post, my bad*

---

### Post by Jetro on 2010-11-22
Okay, so deactivating swap via GParted took forever, but it worked through Terminal. What next?

---

### Post by MooPi on 2010-11-22
Try ```
sudo mke2fs -n /dev/sda5
```
Post results------
Going to walk dog be back in 20 min.

---

### Post by Jetro on 2010-11-22
Good dog xD

Alas, same results as last time
```
sudo mke2fs -n /dev/sda5
mke2fs 1.41.12 (17-May-2010)
/dev/sda5 is apparently in use by the system; will not make a filesystem here!
```
](*,)

---

### Post by MooPi on 2010-11-22
Okay I give up, might as well give testdisk a try.

---

### Post by Jetro on 2010-11-22
Grr. Trying to install testdisk.

```
testdisk
The program 'testdisk' is currently not installed. You can install it by typing:
sudo apt-get install testdisk
```

```
sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Unable to locate package testdisk
```

I even did ```
sudo pico /etc/apt/sources.list
```
and uncommented the multiverse entries (which it said I needed).

---

### Post by Jetro on 2010-11-22
Screw this, I'm going to try to mount the partition from Slax.

Edit, from Slax:
```
e2fsck -p /dev/sda5
/dev/sda5: recovering journal
/dev/sda5 contains a file system with errors, check forced.
/dev/sda5: 240249/612000 files (1.2 % non-contiguous), 2308838/2445896 blocks
```

But when I now open the partition, there are no files or folders in it...

**Victory edit**:
Oh my god, it worked!
After doing the e2fsck check, I followed [Richard Path's advice](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/668561?comments=all)
```
e2fsck -y -f -v /dev/sda5
```
, rebooted, and Ubuntu was back to normal! Not a file or setting missing! :D

I appreciate all the help you've given me, MooPi. ^_^

---

### Post by Jinda on 2011-04-01
Thank you!!!
I had an unclean shutdown while booting from USB. I was getting stuck at an initramfs prompt. Any attempt to mount of fsck my /dev/sda1 failed. With Slack the first attempt failed, but when I changed to /dev/**h**da1, fsck worked and fixed all the errors and after reboot everything was back to normal.

---

