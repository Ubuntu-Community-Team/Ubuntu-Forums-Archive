---
title: "unetbootin doesn't see the fat32 partition on my external hd"
date: 2012-03-26
forum: General Help
---

### Post by AgelessDrifter on 2012-03-26
edit: please see second post. You can ignore this one.


I'm trying to install gparted-live onto my external hd. I made a 1.99 (shot for 200 but 199 is what gparted settled on when I made the partition) fat32 partition on the drive. When I run unetbootin, no drives show up at all when 'type' is set to 'USB'. Dunno what could be up. The rest of that drive is NTFS and it doesn't spot that, either, but I assume that's because it knows I'm installing an ISO so it's only looking for fat32 partitions.

Ubuntu in general finds the drive and the partition -- I've been able to mount it (although I haven't tried writing to it yet), but unetbootin doesn't see it whether it's mounted or not (I assume it shouldn't be, but I figured I'd try).

Any advice is appreciated.

---

### Post by AgelessDrifter on 2012-03-27
Bumping this thread. Shorter. more general question: If I want to run gparted live from my external hard drive to resize the partitions on my internal ones, can I do that, and if so, how? usb-creator-gtk also doesn't see the drive.

The only instructions I could find for doing this start with "boot the OS on the drive". My external HD doesn't have an OS on it, and I don't care to put one on there.

Please help. This is the third consecutive time I've posted a question here and been completely ignored.

---

### Post by idoitprone on 2012-03-27
> **AgelessDrifter said:**
> Bumping this thread. Shorter. more general question: If I want to run gparted live from my external hard drive to resize the partitions on my internal ones, can I do that, and if so, how? usb-creator-gtk also doesn't see the drive.

The only instructions I could find for doing this start with "boot the OS on the drive". My external HD doesn't have an OS on it, and I don't care to put one on there.

Please help. This is the third consecutive time I've posted a question here and been completely ignored.

some of us dont use usb-creator-gtk, because it only work with ubuntu iso files

get unetbootin, there one in ubuntu repos and 
here for windows and etc
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

remember the flash drive must be mounted and fat32 in order for unetbootin to work
i dont think that unetbootin would work with ntfs

install the iso file on a fat32 file system

go to bios and boot external flash drive

---

### Post by AgelessDrifter on 2012-03-27
Thanks for the reply, but unetbootin was my first attempt (see first post). It didn't find either partition on the external hard drive, mounted or unmounted, and I wasn't able to discover why.

edit: ALSO, semi-related -- I just found the ubuntu disk utility and figured I'd make the fat32 partition of the external hd in question bootable to see if that helped in some way. It's taken like 12 minutes already and there's no progress bar/no sign of when it might stop or if it's caught in a loop. I'm afraid to interrupt it. startup dink creator says not enough room on the partition, so I'm going to have to delete it anyway. Is it normal for it to take this long? The partition is 209mb (I dunno if that makes a difference).

---

### Post by idoitprone on 2012-03-27
> **AgelessDrifter said:**
> Thanks for the reply, but unetbootin was my first attempt (see first post). It didn't find either partition on the external hard drive, mounted or unmounted, and I wasn't able to discover why.

post output of 
```
blkid
``````
mount
```if your usb is mounted 

did you run it with root parmission after the usb is mounted
unetbootin s weird like that

```
sudo unetbootin
```?

---

### Post by kdane4 on 2012-03-27
hello,

instead of "set to usb", do you see your partition if its set to hard disk in unetbootin?

---

### Post by AgelessDrifter on 2012-03-27
kdane, the only thing listed under hard disk is the drive named "/"

idoitprone:

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joe)
/dev/sdb2 on /media/gparted_liv type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
/home/joe/Downloads/gparted-live-0.12.0-5.iso on /tmp/tmpeQ7Ny1 type iso9660 (ro)

```

```
/dev/sda1: LABEL="TOSHIBA System Volume" UUID="7EE08D83E08D427F" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004830V03" UUID="B6F28FF6F28FB95F" TYPE="ntfs" 
/dev/sda5: UUID="e6b30895-a7b7-46ea-9e58-806371a22a97" TYPE="ext4" 
/dev/sda6: UUID="301fadfe-0dbf-48ba-9570-6ea24bfcc47b" TYPE="swap"
```


I tried re-opening unetbootin with sudo, and it's the same deal

---

### Post by oldfred on 2012-03-27
If you want an advanced method that once you do it is easy to use and allows more than one ISO per flash drive just install grub2 to the flash drive. I have used FAT, NTFS & ext4 (with journal turned off) and just installed grub2 and copied (not installed like you normally do) the ISOs to the flash drive. The only issue is you have to manually create the grub.cfg with the correct path to the ISO.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Among my grub2 entries I have two gparted versions. I cannot tell the difference but one works and the other does not. It may just be a space at the end of a line or something else equally difficult to debug. But one works. # or commented out lines are where I was testing different things.

grub.cfg
```
menuentry "Gparted live" {
#  insmod loopback
#  insmod iso9660
#  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile nomodeset
  initrd (loop)/live/initrd.img
}

# boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash
menuentry "Gparted Live ISO" {
set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs nomodeset
initrd (loop)/live/initrd.img
}

```

---

### Post by AgelessDrifter on 2012-03-28
thanks, oldfred. That looks a little complicated, but I'll read into it.

Before I go to the trouble, though, will a LiveCD of gparted on my external even allow me to edit my internal? Also, since grub is also used for editing partitions, can I simply install that on the external hd and then *not* install the gparted-live, and use grub2 to repartition my internal hd instead?

Thanks again. I appreciate everyone's input so far.

---

### Post by idoitprone on 2012-03-28
> **AgelessDrifter said:**
> kdane, the only thing listed under hard disk is the drive named "/"

idoitprone:

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joe)
/dev/sdb2 on /media/gparted_liv type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
/home/joe/Downloads/gparted-live-0.12.0-5.iso on /tmp/tmpeQ7Ny1 type iso9660 (ro)

``````
/dev/sda1: LABEL="TOSHIBA System Volume" UUID="7EE08D83E08D427F" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004830V03" UUID="B6F28FF6F28FB95F" TYPE="ntfs" 
/dev/sda5: UUID="e6b30895-a7b7-46ea-9e58-806371a22a97" TYPE="ext4" 
/dev/sda6: UUID="301fadfe-0dbf-48ba-9570-6ea24bfcc47b" TYPE="swap"
```I tried re-opening unetbootin with sudo, and it's the same deal

Oh wise Oldfred, do you have a clue why the usb is mounted but is not picked up by blkid.

Ageless, i wonder if it is a kernel bug? 
plugin the usb and paste the result of
```
dmesg | tail
```I am little interested

wait i had a strange thought
is tis external hdd an gpt partition table?
If so, then most of these utilities cannot read a gpt parition table, change it too mbr which means reformat then unetbootin will start working again

---

### Post by AgelessDrifter on 2012-03-28
```
[158460.160083] wlan0: authenticate with 00:18:6e:5f:56:00 (try 1)
[158460.164411] wlan0: authenticated
[158460.176337] wlan0: associate with 00:18:6e:5f:56:00 (try 1)
[158460.204934] wlan0: RX ReassocResp from 00:18:6e:5f:56:00 (capab=0x421 status=0 aid=2)
[158460.204944] wlan0: associated
[158579.699982] wlan0: authenticate with 00:14:7c:8f:a4:40 (try 1)
[158579.705749] wlan0: authenticated
[158579.720518] wlan0: associate with 00:14:7c:8f:a4:40 (try 1)
[158579.727241] wlan0: RX ReassocResp from 00:14:7c:8f:a4:40 (capab=0x421 status=0 aid=1)
[158579.727251] wlan0: associated

```

I don't think it's a gpt partition table. The whole drive was NTFS when I started, and I've since wiped the whole drive and put on an NTFS partition and a very small FAT32 partition using gparted.

---

### Post by oldfred on 2012-03-28
I have had gparted not show my entire sda drive when XP in sda still booted. I then ran chkdsk and gparted showed it and XP booted a tad faster (4 min instead of 5).

I have a bios_grub partition (gpt drive) that does not show in blkid, but another drive's bios_grub does show. In gparted the one without the UUID has a gparted partition error flag (unknown).

So I might try chkdsk on both the FAT and the NTFS partitions from a Windows repairCD or Windows install.

---

### Post by dragonfly41 on 2012-03-28
does **testdisk** (running as root) see your USB drive?

---

### Post by WasMeHere on 2012-03-28
Hi,

This is just a wild guess: What Unetbootin version are you running and from what operating system? Remember that Windows only can see the first partition in a USB drive!

If you install Unetbootin into Ubuntu, it can see and use any of the primary partitions. I often use the second one for the live system, so that the first partition can be used from Linux and Windows to read and write data.
```
sudo apt-get install unetbootin
```

Have fun finding out :-)
Olle

---

### Post by AgelessDrifter on 2012-03-28
testdisk sees the drive and both partitions. It says the FAT32 partition is primary bootable, which is odd because I made it bootable, but disk utility threw me an error, so I wiped the whole drive and replaced the partitions, but I never went back and made the fat32 partition bootable again.

---

### Post by WasMeHere on 2012-03-28
I think you need to test various methods and theories of what can be causing your problem, but I really have no idea of what it can be.

Have you tried to access your USB drive from another computer and/or another operating system? Or have you tested your USB ports with another USB drive (HDD or flash drive)?

Do you have any data on your USB drive, that you need to save? If this is the case, I think you should back it up now, or try to recover it.

Then I suggest that you try to repartition the drive from the beginning with gparted. And you must boot your system from another drive in order to do it properly. If this does not work, there is something wrong with the connection or the drive itself.

---

### Post by AgelessDrifter on 2012-03-28
The drive is external, and everything I've been trying has been through ubuntu booting from my laptop's internal hard drive. There is no data on the external -- the most recent thing I tried was to wipe it and repartition it (through ubuntu booted from my internal drive) with gparted, but the outputs I've posted in this thread have all come after that, so that didn't fix it.

The drive was working in Windows 7 before I started trying to get gparted-live on there, but I haven't tried it since. I'll try again now and report the results. The drive has been mountable and has had data on and off it through ubuntu -- at one point it was showing up in both lspci and blkid, so I don't think it's the connection to the drive.

---

### Post by idoitprone on 2012-03-28
> **AgelessDrifter said:**
> ```
[158460.160083] wlan0: authenticate with 00:18:6e:5f:56:00 (try 1)
[158460.164411] wlan0: authenticated
[158460.176337] wlan0: associate with 00:18:6e:5f:56:00 (try 1)
[158460.204934] wlan0: RX ReassocResp from 00:18:6e:5f:56:00 (capab=0x421 status=0 aid=2)
[158460.204944] wlan0: associated
[158579.699982] wlan0: authenticate with 00:14:7c:8f:a4:40 (try 1)
[158579.705749] wlan0: authenticated
[158579.720518] wlan0: associate with 00:14:7c:8f:a4:40 (try 1)
[158579.727241] wlan0: RX ReassocResp from 00:14:7c:8f:a4:40 (capab=0x421 status=0 aid=1)
[158579.727251] wlan0: associated

```I don't think it's a gpt partition table. The whole drive was NTFS when I started, and I've since wiped the whole drive and put on an NTFS partition and a very small FAT32 partition using gparted.

partition table and filesystem is not the same. Partition tabel manages the filesystem. NTFS and fat is a file system while mbr and gpt is a partition table

to check, you have install some utilities
```
sudo apt-get install gdisk
```

to check post output of 
```
sudo gdisk -l /dev/sdb
```

gparted is gpt aware but i am not so sure about unetbootin
Wiping your flash drive does not mean you wipe the partition table. You have to explictly change it

---

### Post by AgelessDrifter on 2012-03-28
Here's the output of that command, idoit.

```
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sdb: 976773167 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F6B73A21-23A3-4C0E-BF70-A168B6BFD7ED
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773133
Partitions will be aligned on 2048-sector boundaries
Total free space is 2028 sectors (1014.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          514047   250.0 MiB   0700  Linux/Windows data
   2          514048       976773119   465.5 GiB   0700  Linux/Windows data

```

"found invalid GPT and valid MBR makes me nervous. Any ideas what that's about?


I tried the drive on Windows 7. Windows found it. I tried installing gparted live on the drive through tuxboot on Windows, and that went off without a hitch, but when I rebooted, the Toshiba screen with "press F12 for boot menu" froze before I pressed anything.

I wiped the drive with gparted on linux, then reinstalled gparted live with tuxboot through windows again. Same result -- boot screen freezes immediately if the drive is plugged in.

---

### Post by oldfred on 2012-03-28
If drive was gpt and you install Windows it converts back to MBR but only overwrite the primary gpt partition table. One of the advantages of gpt is that it has a backup to the partition table and Windows does not erase the backup. Linux tools see the backup and get confused if MBR or gpt.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by idoitprone on 2012-03-28
> **AgelessDrifter said:**
> Here's the output of that command, idoit.

```
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sdb: 976773167 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F6B73A21-23A3-4C0E-BF70-A168B6BFD7ED
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773133
Partitions will be aligned on 2048-sector boundaries
Total free space is 2028 sectors (1014.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          514047   250.0 MiB   0700  Linux/Windows data
   2          514048       976773119   465.5 GiB   0700  Linux/Windows data

```"found invalid GPT and valid MBR makes me nervous. Any ideas what that's about?


I tried the drive on Windows 7. Windows found it. I tried installing gparted live on the drive through tuxboot on Windows, and that went off without a hitch, but when I rebooted, the Toshiba screen with "press F12 for boot menu" froze before I pressed anything.

I wiped the drive with gparted on linux, then reinstalled gparted live with tuxboot through windows again. Same result -- boot screen freezes immediately if the drive is plugged in.

no its fine. It either gpt or mbr. It says that it is a mbr partition table. So, I'm stump, however, why does it have 2 partitions? Does your harddrive have special hidden programs that is preventing linux tools to read it?

---

### Post by AgelessDrifter on 2012-03-28
oldfred: I haven't installed Windows or any OSes on the drive. It had an NTFS partition on it -- I guess within a gpt table -- when I got it, and I've deleted that partition and replaced it using gparted. Would that cause the MBR/GPT confusion?

idoit: Both partitions are empty and put there by me. It's a good-sized drive, and I want to use the rest of the space for general file storage. The small partition is for the gparted live installation, which has to have FAT32, apparently. But I don't want the other files on a FAT32 partition and I don't want the gparted live installed on the same partition as the files I want to store, that's all.

---

### Post by WasMeHere on 2012-03-29
I have to admit that I don't understand the problem of your external HDD, so I am reading and learning...

---

### Post by oldfred on 2012-03-29
If it was gpt and you used gparted to repartition, not Windows then I would normally think it is ok. But you got the warning message on gpt data. 

Did you try fixparts? It may tell more.

I think my previous post was directly booting ISO from a USB flash drive. But you can do the same from a hard drive. I never had an install go so fast as one from a spinning hard drive ISO to my new SSD. I had thought the USB flash installs were quick compared to CDs. :)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

