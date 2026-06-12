---
title: "Error 13: Invalid or Unsupported Executable format"
date: 2010-05-16
forum: General Help
---

### Post by Canterwood on 2010-05-16
Hello Ubuntu-forum!

This is a repost, since I put it in the wrong subforum first.
I've been googling all afternoon to fix this error I get (the one in the thread title). The situation is as follows:

I have multiple harddrives (3x320gb and 1x160gb) all on the SATA interface. One of these drives contains Windows, and the rest I use for programs and downloads. I've installed Ubuntu 9.04 from a USB-stick using the installer's partitioner to make some room for Ubuntu (Ext4 filesystem).

This error shows it's ugly face after selecting Windows 7 in the Grub bootloader menu.

I am a complete Linux newbie, but I've tried Ubuntu and SUSE in the past. Still, I'm not nearly savvy enough to fix a problem like this. I don't know what information to post to help you guys figure this out, but when you ask I'll be happy to post any logs you might need. Thanks in advance!

---

### Post by sgosnell on 2010-05-16
What is happening?  What do you do to get this error?  If you're trying to run a .exe file from Linux, it won't work, those only can run from Windows.

---

### Post by Canterwood on 2010-05-16
> **sgosnell said:**
> What is happening?  What do you do to get this error?  If you're trying to run a .exe file from Linux, it won't work, those only can run from Windows.

I get this error after I start my computer and enter the Grub loader. There, I select Windows to start it, and it won't. Instead, I get this "Error 13".

---

### Post by Canterwood on 2010-05-16
Also, I have a dualscreen setup. YouTube won't go fullscreen. It does switch to a fullscreen player, but the video itself doesn't stretch out over it. Instead, I just get it in the same size, and the rest of the screen goes black.

---

### Post by Canterwood on 2010-05-16
Could I please get some help? I know I seem impatient, but it's pretty important I get back into Windows.

---

### Post by Canterwood on 2010-05-16
Ok, I thought maybe this could help. I've edited my /boot/grub/menu.lst to point it to my Windows 7 installation. Now Grub tells me: Error 15, file not found.
 
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b50a194c-b389-483d-8db7-e3739256e3ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b50a194c-b389-483d-8db7-e3739256e3ca

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		b50a194c-b389-483d-8db7-e3739256e3ca
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=b50a194c-b389-483d-8db7-e3739256e3ca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		b50a194c-b389-483d-8db7-e3739256e3ca
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=b50a194c-b389-483d-8db7-e3739256e3ca ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b50a194c-b389-483d-8db7-e3739256e3ca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b50a194c-b389-483d-8db7-e3739256e3ca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b50a194c-b389-483d-8db7-e3739256e3ca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b50a194c-b389-483d-8db7-e3739256e3ca ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b50a194c-b389-483d-8db7-e3739256e3ca
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
uuid		/dev/sdb1
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by sgosnell on 2010-05-16
How did you edit the file, what changes did you make?  Is the Windows drive in fact hd0.0?  That should be /dev/sda1, I think.  There are a number of threads on the forum that discuss editing grub to get a dual boot working, and you probably should read them.

---

### Post by Canterwood on 2010-05-16
> **sgosnell said:**
> How did you edit the file, what changes did you make?  Is the Windows drive in fact hd0.0?  /dev/sdb1 is not a uuid, but it might work.  I'm far from an expert on this.  There are a number of threads on the forum concerning making dual boots work, and you probably should try reading them.

I changed the title from Windows Vista (loader) to Windows 7, added makeactive and added the uuid. How can I find out whether hd(0,0) is the one containing Windows? I can find and mount it from Linux, but I don't know where I can find that information for a mounted drive.

---

### Post by sgosnell on 2010-05-16
hd0,0 is the first partition of the first drive, and would usually be mounted as /dev/sda1.  I don't dual-boot, so I don't have info on this handy.  I would suggest reading the forum archives by searching for dual boot and grub.

---

### Post by Canterwood on 2010-05-16
> **sgosnell said:**
> hd0,0 is the first partition of the first drive, and would usually be mounted as /dev/sda1.  I don't dual-boot, so I don't have info on this handy.  I would suggest reading the forum archives by searching for dual boot and grub.

Will do, thanks!

---

### Post by Canterwood on 2010-05-17
Hey there forum

So I'm at work right now (at a computer shop of all places, heavily Windows-based sadly) and I decided to check up on my thread. Sad to see no response. When I get back home I'll try and update you guys on what I found! In the mean time, you're always welcome to respond here! Again, thanks in advance.

---

### Post by Canterwood on 2010-05-17
Okay, it seems like I have found a lead. Please tell me if I'm wrong!


> Some have many operating systems and install one boot loader to the MBR and each operating system's boot loader to the PBR of that system and chainboot all the others from the first. Grub2 does not like to be installed to a PBR - something about blocklists and less reliable, but old grub works just fine in a PBR.

So if you overwrite the windows boot loader in the windows PBR - boot sector then windows will not boot.

Source: Post #6 in [http://ubuntuforums.org/showthread.php?t=1484410&highlight=windows+grub](http://ubuntuforums.org/showthread.php?t=1484410&highlight=windows+grub)

---

### Post by Canterwood on 2010-05-17
It seems I have made some progress. I have installed kgrubeditor and started it, and the program recommended I change the Windows entry from hd(0,0) to hd(2,0). I did so, and now when I boot and select Windows from the boot menu, I get a message showing:
 
Starting up...

_
 
Where the cursor will just blink. No boot yet, but I feel like I'm getting closer. Feel free to chime in!

---

### Post by angry_johnnie on 2010-05-17
the problem seems to be that grub is not finding windows where it's being told it is.

to find out, boot into linux, open a terminal and run

```
sudo fdisk -l
```

that would yield, for example, something like this:

```
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        6527    41945715    7  HPFS/NTFS
/dev/sda3            6528       24792   146713582    f  W95 Ext'd (LBA)
/dev/sda5            6528        6654     1020096   82  Linux swap / Solaris
/dev/sda6            6655        9204    20482843+  83  Linux
/dev/sda7            9205       24792   125210578+   7  HPFS/NTFS

```

what you're looking for is the NTFS partitions.  just note where they are.  and then you need to find that partition's identifier, by running (for example):

```
sudo blkid /dev/sda1
```

which would yield something like this, for example:

```
/dev/sda1: LABEL="XP" UUID="57CB65D535BFA493" TYPE="ntfs"
```


now you can copy that uuid and paste it on your /boot/grub/menu.lst file so that your windows entry reads:
```

title		Windows 7
uuid		whatever the blkid command yielded as uuid
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader     +1
```


i'm not really sure, but i think (i'm almost sure) you culd just delete the uuid line on that entry.  you're already telling it where it is with the rootnoverify line, so why bother telling it again?

hope that helps

---

### Post by Canterwood on 2010-05-17
> **angry_johnnie said:**
> the problem seems to be that grub is not finding windows where it's being told it is.

to find out, boot into linux, open a terminal and run

```
sudo fdisk -l
```

that would yield, for example, something like this:

```
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        6527    41945715    7  HPFS/NTFS
/dev/sda3            6528       24792   146713582    f  W95 Ext'd (LBA)
/dev/sda5            6528        6654     1020096   82  Linux swap / Solaris
/dev/sda6            6655        9204    20482843+  83  Linux
/dev/sda7            9205       24792   125210578+   7  HPFS/NTFS

```

what you're looking for is the NTFS partitions.  just note where they are.  and then you need to find that partition's identifier, by running (for example):

```
sudo blkid /dev/sda1
```

which would yield something like this, for example:

```
/dev/sda1: LABEL="XP" UUID="57CB65D535BFA493" TYPE="ntfs"
```


now you can copy that uuid and paste it on your /boot/grub/menu.lst file so that your windows entry reads:
```

title		Windows 7
uuid		whatever the blkid command yielded as uuid
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader     +1
```


i'm not really sure, but i think (i'm almost sure) you culd just delete the uuid line on that entry.  you're already telling it where it is with the rootnoverify line, so why bother telling it again?

hope that helps

First of all, thank you very much for your reply. In the mean time, I have done some of my own stuff.

First, I mapped (hd2) to (hd0) as some guides on the internet told me that Windows won't want to boot if it doesn't think it's on the first drive. This has yielded some results. Now, it hangs at "Starting up" with the extra message "BOOTMGR is missing" which I recognize as a Windows error. Still, here are my results for the same commands.

sudo fdisk -l:


```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c87c10a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306487046    7  HPFS/NTFS
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
117 heads, 43 sectors/track, 124258 cylinders
Units = cylinders of 5031 * 512 = 2575872 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       40708   102400952+   7  HPFS/NTFS
/dev/sdb2           40709      124257   210167509+   f  W95 Ext'd (LBA)
/dev/sdb5           40709      124257   210167488    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       33982   272960383+  83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x063c8a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19457   156288321    7  HPFS/NTFS
```

I think my Windows 7 partition is on /dev/sdb1. So here's the output for sudo blkid /dev/sdb1:

```
/dev/sdb1: UUID="86D0EAC6D0EABB95" TYPE="ntfs" 
```

I'll try this UUID and remove the mappings I had made. *Crosses fingers*

UPDATE: Using the UUID, grub tells me "File not found".

---

### Post by angry_johnnie on 2010-05-17
darn...

if windows 7 is on /dev/sdb1

then, to grub, it would be on hd1,0

so try this and see what happens:

```
title		Windows 7
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by Canterwood on 2010-05-17
> **angry_johnnie said:**
> darn...

if windows 7 is on /dev/sdb1

then, to grub, it would be on hd1,0

so try this and see what happens:

```
title		Windows 7
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader     +1
```

Tried that just now. I get Error 15: File not found.

When I had it set to hd2,0 and mapped them like so:

map (hd0) (hd2)
map (hd2) (hd0)

It told me Starting up... BOOTMGR is missing.

Doesn't this indicate that I'm pointing to the correct partition, but somehow the Windows bootmanager was corrupted?

---

### Post by angry_johnnie on 2010-05-17
:o

if windows' boot loader is missing, or corrupt, you might want to look at [this]("http://support.microsoft.com/kb/927392")

although that would hose grub.

---

### Post by Canterwood on 2010-05-17
Hmm, according to post #4 in this thread: [http://ubuntuforums.org/showthread.php?t=1159205](http://ubuntuforums.org/showthread.php?t=1159205)
there is supposed to be an 8MB partition which I should point grub to.

How do I find that partition, and point grub to it? I suspect it's /dev/sdb2 because of the weird file system name, but how can I see what size it is? And what does grub call /dev/sdb2?

UPDATE: Tried (hd1,1) but alas. No cigar.
UPDATE: No luck with (hd2,1) either.

---

### Post by Canterwood on 2010-05-17
Well, I think I found the problem (assuming the guy in post #4 on [http://ubuntuforums.org/showthread.php?t=1159205](http://ubuntuforums.org/showthread.php?t=1159205) is correct)

In Windows, I had 5 partitions. I instructed the partition manager that comes with the Ubuntu installation to make a new partition on one of my disks by splitting it up.

Using the pre-boot Grub menu I exhausted all the options (hd0,0; hd1,0; hd1,4; hd2,0; hd3,0 and hd3,4). These are six partitions.

If I'm not mistaken, Linux requires 2 partitions. The main one, and a swap partition. So the total would amount to 7 (Windows' 5 plus Linux' 2).

Could it be that Windows stored it's hidden boot partition on the drive I put Linux (or it's swap partition) on? If so, would I be saved by making a new boot partition for Windows using a restore disk?

I'm just taking a shot in the dark here. Any advice would be much  appreciated. Again, I have no problem posting logs or terminal output. Thanks in advance!

---

