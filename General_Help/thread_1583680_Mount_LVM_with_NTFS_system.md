---
title: "Mount LVM with NTFS system"
date: 2010-09-28
forum: General Help
---

### Post by tinkerbox on 2010-09-28
I tried few command to mount NTFS system that I know works....but mount LVM with NTFS like this absolutely failed me....

Commands that I tried...
```

mount -o loop,offset=32256 /dev/storage/games /windows
mount -o loop,offset=32256 /dev/storage/games5 /windows
mount -t ntfs-3g /dev/storage/games /windows
mount -t ntfs-3g /dev/storage/games5 /windows
mount -t ntfs -o nls=utf8,umask=0222 /dev/storage/games /windows
mount -t ntfs -o nls=utf8,umask=0222 /dev/storage/games5 /windows

```

This is LVM i want to mount...
```

fdisk -l /dev/storage/games

Disk /dev/storage/games: 1099.5 GB, 1099511627776 bytes
255 heads, 63 sectors/track, 133674 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48e094b4

             Device Boot      Start         End      Blocks   Id  System
/dev/storage/games1               2      133673  1073720340    f  W95 Ext'd (LBA)
/dev/storage/games5               2       78326   629145531    7  HPFS/NTFS
/dev/storage/games6           78327      133673   444574746    7  HPFS/NTFS
```

It this possible to mount???

ps: posting on forums is always been my last resort after search...

---

### Post by srs5694 on 2010-09-28
You've got something rather unusual there, and I don't think it's a Logical Volume Manager (LVM) configuration. I don't see any /dev/storage directory on any of my systems, so I suspect you've got a custom udev rule set up that creates a symbolic link from /dev/storage/games to some more conventional device file on your computer. Have you edited any files in the /etc/udev/rules.d directory? If so, what did you change? Alternatively, what's the output of "ls -l /dev/storage/*"?

If I'm right, one of the commands you reported ("mount -t ntfs-3g /dev/storage/games5 /windows") might work, but only if executed as root, so you'd need to add "sudo" to the front of that command. If that doesn't work, post the exact error message that this commnd produces. It's possible that a /dev/storage/games device file exists, but not /dev/storage/games5, in which case the command won't work. It's probably better to simplify by not using non-standard symbolic links and just referring to it as /dev/sdb5 or whatever the main device filename is.

---

### Post by tinkerbox on 2010-09-28
/dev/storage is my LVM pool

```
# ls -l /dev/storage/
total 0
lrwxrwxrwx 1 root root 23 2010-09-29 09:09 games -> ../mapper/storage-games
lrwxrwxrwx 1 root root 21 2010-09-29 09:09 mix -> ../mapper/storage-mix

# ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 60 2010-09-29 09:09 control
brw-rw---- 1 root disk 252,  0 2010-09-29 09:09 storage-games
brw-rw---- 1 root disk 252,  1 2010-09-29 09:09 storage-mix


cfdisk (util-linux-ng 2.16)

                                           Disk Drive: /dev/mapper/storage-games
                                            Size: 1099511627776 bytes, 1099.5 GB
                                   Heads: 255   Sectors per Track: 63   Cylinders: 133674

      Name              Flags             Part Type       FS Type                   [Label]                Size (MB)
 --------------------------------------------------------------------------------------------------------------------------
                                           Pri/Log        Free Space                                            8.23
      storage-games5                       Logical        NTFS                      [J]                    644245.06
      storage-games6                       Logical        NTFS                      [4]                    455244.58
                                           Pri/Log        Free Space                                            8.23

```

Some errors:
```

# mount -t ntfs-3g -o loop,offset=32256 /dev/mapper/storage-games /windows/
NTFS signature is missing.
Failed to mount '/dev/loop17': Invalid argument
The device '/dev/loop17' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

# mount -o loop,offset=32256 /dev/mapper/storage-games /windows/
mount: you must specify the filesystem type

# mount -o loop,offset=32256 /dev/mapper/storage-games6 /games_master_drv_y/
/dev/mapper/storage-games6: No such file or directory

```

Could it be because it's **logical disk** NTFS volume disk?

I could mount disk with ntfs filesystem
I could mount file image with ntfs filesystem
I could mount LVM volume with linux filesystem
BUT not LVM with ntfs.... :cry:

fyi: LVM is on softraid 10, and I have huge list of games and movies on it.....1.4TB....

I just want to how if this possible to mount and how to do this...

---

### Post by srs5694 on 2010-09-29
Is this a Linux LVM you've got, or is it something else, like a Windows LDM? I ask for two reasons:


[list]
[*]I've never before heard of anybody creating partitions inside a logical volume, which is what you've done. The whole point of an LVM configuration is to enable filesystem management that's much more flexible than partitions allow, so creating partitions inside a logical volume defeats the purpose of the LVM. It also adds yet another layer of complexity.
[*]Using NTFS inside a Linux LVM, which is accessible only to Linux, is inadvisable at best. Linux lacks good NTFS maintenance tools, so the moment something goes wrong (a power failure or system crash), Linux is likely to refuse to mount the filesystem, and unless you can find a way to give Windows access to the filesystem, your data will be effectively lost.
[/list]


As to the nitty-gritty of your situation, since you've partitioned the logical volume, if you want access to the partitions in the logical volume, you must create partition identifiers for it, not just logical volume identifiers. Essentially, /dev/mapper/storage-games is like a whole hard disk, so you need /dev/mapper/storage-games1, /dev/mapper/storage-games2, and so on. I believe there's a udev option to create partition identifiers, but I don't recall the details of this.

If you've already stored data in this volume somehow, I recommend you move the data off it using whatever method you used to put it there and then redo the configuration in a simpler and more conventional way, such as creating logical volumes for each of the partitions within the /dev/mapper/storage-games partitions you've created. Use Linux-native filesystems on these logical volumes, not NTFS. This advice, however, is based on the assumption that you're using a Linux LVM; if it's a Windows LDM, I don't know the rules for that.

If you haven't yet copied data into /dev/mapper/storage-games, just delete it and create suitable logical volumes to use directly, as just described.

---

### Post by tinkerbox on 2010-09-29
Thanks for clear explanations, I was on wrong direction and you have show me what I was wrong....Thank you =)

This is linux LVM. I have setup a computer to be my personal storage. I wanted huge storage and at the same time I want my data to be safe, so I installed ubuntu server with 5 hardisks.
1st hardisk - ubuntu server 10.04
4 hardisk - software raid 10 then I setup LVM on this raid

Then I connect this storage from other PCs using Ata Over Enternet(AoE). The reason why I need to storage to be in NTFS window system cos I have installed lots of games on it and tons of movies and anime stored there too. I could share this storage using SAMBA but I cant run most of the games over the network...

I did search before, accessing linux partition on windows, but I couldnt find the success of doing read and write to linux partition from windows. That was last year...I wonder if now this is possible??

I'm going out soon, I will try your suggestion when im back.
I luv ubuntu but I cant migrate myself 100% to ubuntu and leave my games behind :cry:

---

### Post by tinkerbox on 2010-10-02
I do not really understand with "partition identifiers", google it but I think I gave up with my idea...was stupid =)
Instead of setting up LVM on top of softraid, I could just use softraid itself. Cos ntfs will not work on LVM, I mean resizing the size of ntfs partition on LVM... That is not the idea of using LVM. I know, wasnt clear to me when I use LVM for first time.

srs5694,
Thank you =)

---

### Post by srs5694 on 2010-10-02
> **tinkerbox said:**
> I do not really understand with "partition identifiers", google it but I think I gave up with my idea...was stupid =)

By "partition idenfiers," I mean the numbers that follow disk devices. For instance, /dev/sda refers to a whole disk, but /dev/sda1 and /dev/sda2 are two partitions on /dev/sda. In this case, the trailing "1" and "2" are partition identifiers. I'm pretty sure there's a udev option that controls whether these are created for disk devices, but I don't recall offhand what that option is.

> Instead of setting up LVM on top of softraid, I could just use softraid itself. Cos ntfs will not work on LVM, I mean resizing the size of ntfs partition on LVM... That is not the idea of using LVM. I know, wasnt clear to me when I use LVM for first time.

That's a much simpler plan, which is likely to produce much better results.

---

### Post by tinkerbox on 2011-01-14
Im not sure if this works with LVM, I did not try cos im no longer using LVM.... But i did try with image file:
[http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux](http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux)

it works. Just added for future refence and hope it will helps others =)

---

### Post by tinkerbox on 2011-01-14
Im not sure if this works with LVM, I did not try cos im no longer using LVM.... But i did try with image file:
[http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux](http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux)

it works. Just added for future reference and hope it will helps others =)

---

### Post by tinkerbox on 2011-01-14
Im not sure if this works with LVM, I did not try cos im no longer using LVM.... But i did try with image file:
[http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux](http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux)

it works. Just added for future reference and hope it will helps others =)

---

