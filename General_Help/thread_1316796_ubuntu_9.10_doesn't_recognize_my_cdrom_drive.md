---
title: "ubuntu 9.10 doesn't recognize my cdrom drive"
date: 2009-11-06
forum: General Help
---

### Post by kboy on 2009-11-06
well, i've recently installed ubuntu 9.10 on my msi laptop' everything works fine, except it doesn't recognize any cd or dvd disk i enter.

need help

---

### Post by Giblet5 on 2009-11-06
Put a written CD in.

Open a terminal window and enter ```
sudo fdisk -l
```

Post the output, then post the contents of /etc/fstab.

(Do this in a CODE block -- that # gadget on the thread comment editor)

---

### Post by kboy on 2009-11-06
I've entered a music cd, This is my fdisk output, it doesn't even contain a cdrom partition:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd02b4d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+  83  Linux
/dev/sda2            1959        2089     1052257+  82  Linux swap / Solaris
/dev/sda3            2090       30401   227416140   83  Linux

```


and this my fstab output:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b0c6f861-1a27-4f51-b170-d4bd643640fd /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=a098d378-0623-41b7-8538-6ab27eee360e /home           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=20037991-bbdb-42d8-bf7e-791dc332873a none            swap    sw              0       0
```

thanks

---

### Post by Giblet5 on 2009-11-06
Can you hear the CD spin-up when you insert the music CD?

If not, it may not be fully connected, or it may be dead (it happens). Is the CD drive removable? Try removing it and reinserting it.

If it spins-up, the data cable may be disconnected or the drive may be dead.

---

### Post by sisco311 on 2009-11-06
what's the output of:
```
sudo lshw -c disk
```

---

### Post by kboy on 2009-11-06
there is no problem with the cdrom drive, it works, when i enter the ubuntu live cd it works fine when boot it.

this is the output of lshw -c disk:

```
 *-disk                  
       description: ATA Disk
       product: WDC WD2500BEVT-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 11.0
       serial: WD-WXEY08JVA721
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cd02b4d0
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb

```

thank you

---

### Post by Giblet5 on 2009-11-06
Presuming that /dev/sdb is an SD card reader, it's clear that your CD drive is AWOL.


Is this a Blu-Ray player?

Although, mine shows up as ```
*-cdrom:1
       description: DVD writer
       product: BD  B  DH4B1S
       vendor: ATAPI
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 7112
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
```

So that's unlikely to be the problem...

Weird!

---

### Post by kboy on 2009-11-06
My cdrom/dvd drive works fine, I've just checked it using the live ubuntu cd.
Is it possible there is a problem with the cd because i've installed the system using a usb drive???

---

### Post by Giblet5 on 2009-11-06
That wouldn't matter. The hardware would still be visible to the kernel and therefore to the fdisk / lshw commands.

You aren't running a custom-built kernel, are you? That would explain this...

Can you post the output of ```
dmesg
```

We can look for any SCSI errors from boot in that.

---

### Post by sisco311 on 2009-11-06
try to reload the cdrom module:
```
sudo modprobe -r ide-cd
sudo modprobe -r sr-mod
sudo modprobe -r cdrom

sudo modprobe ide-cd
sudo modprobe sr-mod
sudo modprobe cdrom

```

and post the output of:
```
dmesg | tail -n 20
```

---

### Post by kboy on 2009-11-06
when i try to load the cdrom module it gives me an error:

```
FATAL: Module ide_cd not found.
```

or 

```
FATAL: Module sr_mod not found.

```

---

### Post by Giblet5 on 2009-11-06
Well there's your problem.

Bring up synaptic. Search for linux-image.

Mark the latest image for reinstall.

Click apply.

Try the modprobe commands again.

---

### Post by kboy on 2009-11-06
> **Giblet5 said:**
> Well there's your problem.

Bring up synaptic. Search for linux-image.

Mark the latest image for reinstall.

Click apply.

Try the modprobe commands again.

it didn't work, i've installed the linux-image but the modules still fail.
here is the dmesg | tail -n 20, output, without loading the modprobe:

```
[   26.593755] [drm] TV-16: set mode NTSC 480i 0
[   26.863432] [drm] TV-16: set mode NTSC 480i 0
[   27.011201] [drm] TV-16: set mode NTSC 480i 0
[   27.260712] CPU0 attaching NULL sched-domain.
[   27.260717] CPU1 attaching NULL sched-domain.
[   27.276120] CPU0 attaching sched-domain:
[   27.276126]  domain 0: span 0-1 level MC
[   27.276130]   groups: 0 1
[   27.276139] CPU1 attaching sched-domain:
[   27.276143]  domain 0: span 0-1 level MC
[   27.276147]   groups: 1 0
[   30.524848] [drm] TV-16: set mode NTSC 480i 0
[   30.665212] [drm] TV-16: set mode NTSC 480i 0
[   47.914679] wlan0: authenticate with AP 00:1b:11:a2:08:48
[   47.916161] wlan0: authenticated
[   47.916164] wlan0: associate with AP 00:1b:11:a2:08:48
[   47.918024] wlan0: RX AssocResp from 00:1b:11:a2:08:48 (capab=0x421 status=0 aid=1)
[   47.918027] wlan0: associated
[   47.918589] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   58.164104] wlan0: no IPv6 routers present

```

---

### Post by kboy on 2009-11-06
maybe i should try to reinstall ubuntu?

---

### Post by brundles on 2009-11-07
Same issue here - drive doesn't show through any hardware checks (fdisk, lshw, etc). Same errors with the modprobe too.

This is on a system that had a clean Karmic install this morning with no errors. The drive works fine when booted to Windows and even from the BIOS with the boot disc.

Any thoughts appreciated!

---

### Post by JeanB on 2009-12-01
Hi Kboy and Brundles,

I have exactly the same problem with the same modprobe error.
Did you find the solution or are you still both  with your CD/DVD driver AWOL?

So I am very interested in reading about you.

Best thoughs

---

### Post by Copernicus1234 on 2009-12-01
Same problem here.

CD-rom worked during installation but is not detected in Gnome.

---

### Post by JeanB on 2009-12-04
Uppp!!

---

### Post by Copernicus1234 on 2009-12-06
I found out you can manually mount the drive by typing this in the terminal:

```
sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

Type this to unmount:

```
sudo umount /media/cdrom
```

---

### Post by JeanB on 2009-12-08
Well,

"sudo mount -t iso9660 /dev/cdrom /media/cdrom"

="mount: no media found in /dev/sr0"

Thanks a lot for thinking in desperated Ubunteros

---

### Post by tkearn5000 on 2009-12-08
Similar problem here. My cd/dvd drive shows up in nautilus. but when i click on properties, it knows nothing about it. When i insert a cd or dvd, it spins up, but after that nothing happens. I cannot mount it, or see what was on the disc. Any one figure this one out yet?

I'm also curious if this is a laptop problem. I have a dell studio 15 with a slot loading drive. I can't even eject a disc once I put it in without rebooting, and ejecting during startup. I've tried numerous ways, including from the terminal.

---

### Post by jeffbarish on 2009-12-13
Check to see whether you are in the cdrom group.

---

### Post by jerome schatten on 2009-12-14
I had a similar problem; that is: the drive would read a data disk but not an audio disk. If you put a data disk in the drive other than the live cd, does the system mount the drive?

If it does mount the data disk and you can access it, then I suspect a drive problem. These drives, to my limited knowledge, use a different lasers for audio and data. 

If the data disk mounts successfully, you should see that the mounted file system is iso9660 on the output of 'lshw -c disk' for the cdrom drive.

Now I see two possibilities: 
1. the drive is truly defective; try replacing it. (of course try re-seating the cables and replacing cables first).
2. It may be a SATA cdrom interface; change it to ide if it has both. (I can't remember your configuration).

The problem with mine was the second: there was a screw up in the SATA interface -- apparently, the SATA standards are not universally implimented the same way it seems. It took me a week to find the problem (replace the drive with one that had an ide PATA controller interface.

My terminology may be a bit fouled up as I am not a wizard.

Hope this helps a bit,
jerome

---

### Post by JeanB on 2009-12-19
:guitar:
HI Jerome an all of you.
YEAPAAA!!! I've found "my" solution. Hoping that it may be useful for many others.
I've just changed my IDE writer for a SATA one....and ALLELUIA! After some frustrating months and multiples interventions in many forums in three languages... YES!!!I've got it!
It is something very easy to do in a PC( it's the first time I opened the tower, so if I did it...) for an acceptable price (around 22 Euros)
In a laptop...?
I remind that the symptoms were ; a driver recognized but without any media found (audio, video, data. NOTHING!)

Merry christmas

Jean-Pierre

---

### Post by jerome schatten on 2009-12-19
> **JeanB said:**
> :guitar:
HI Jerome an all of you.
YEAPAAA!!! I've found "my" solution. Hoping that it may be useful for many others.
I've just changed my IDE writer for a SATA one....and ALLELUIA! After some frustrating months and multiples interventions in many forums in three languages... YES!!!I've got it!
It is something very easy to do in a PC( it's the first time I opened the tower, so if I did it...) for an acceptable price (around 22 Euros)
In a laptop...?
I remind that the symptoms were ; a driver recognized but without any media found (audio, video, data. NOTHING!)

Merry christmas

Jean-Pierre

Bonjour Jean-Pierre...

What a strange world; my symptoms were pretty much the same as yours; my solution: exactly the opposite - rip out the SATA optical drive and replace with an IDE. So it goes. What is the nature of the computer you are using? Mine is a dual core Intel machine with 4 GB ram and two 500 GB hard drives.

Best,
jerome

---

### Post by JeanB on 2009-12-21
Guten Tag Jerome, (just a little bet for fun but I generally never win!)

> 
What a strange world; my symptoms were pretty much the same as yours; my solution: exactly the opposite - rip out the SATA optical drive and replace with an IDE. So it goes. What is the nature of the computer you are using? Mine is a dual core Intel machine with 4 GB ram and two 500 GB hard drives.
Happy to know that you've found "your" solution too.
I have a very basic computer:

AMD Athlon 64 X 2 dual core. 2,6 Ghz
HDD 160 GO
2 GO ram

And it goes really well! Much more than I could imagine!

I saw in forums , looking back in the past, that some Ubunteros have resolved these kinds of problem with ours both solutions but without understanding exactly why it works?!

Wouldn't you be in 32 bits?

Regards,
Jean-Pierre

---

### Post by jerome schatten on 2009-12-21
> **JeanB said:**
> Guten Tag Jerome, (just a little bet for fun but I generally never win!)

Happy to know that you've found "your" solution too.
I have a very basic computer:

AMD Athlon 64 X 2 dual core. 2,6 Ghz
HDD 160 GO
2 GO ram

And it goes really well! Much more than I could imagine!

I saw in forums , looking back in the past, that some Ubunteros have resolved these kinds of problem with ours both solutions but without understanding exactly why it works?!

Wouldn't you be in 32 bits?

Regards,
Jean-Pierre

============

Shalom, and compliments of the season Jean-Pierre...

Yes indeed: 32 bit Intel dual core machine with 4GB ram and two 500GB hd. is what I have here.

What I have is a work-around, such that when the problem rears it's ugly head, I can set it right again. Fortunately, it does not happen too often. I should have stayed with 9.04 where it didn't happen at all.

You are correct, the problem is only understood by the symptoms: high cpu usage by 'udevd'. There are all sorts of 'haywire' schemes that folks have come up with to live with this problem, but no-one has explained the cause. I suspect it will go away in another release but a host of new problems will emerge.

So it goes.
jerome

---

### Post by JeanB on 2009-12-21
Hola Jerome, QUE TAL?

I am really the best!
I told it. I never win. Excepted when I bet on the cleverness and the humour sense of people I don' know...

I think like you. Now that I have the solution, I 'm going to stay a long time calm and cool with my karmic and all the software that goes well. I will fight against the temptation of rushing on the next upgrade. There are peoples much more qualified to sponge these kind of imperfections.Hoping the day I will be one of them... it's a long way.

I hope you the best

Jean-Pierre

---

### Post by Arnaud22 on 2010-04-03
Hello, 
I installed my ubuntu 9.10 from cdrom but can't read any cd or dvd from it being not able to be mounted (error message). I read all the posts of this thread but don't understand all of it because i'm quite new to ubuntu. i wandered if you could advise me on this problem.
Here are the posts that can help you maybe:


"sudo fdisk -l" result in terminal:
arnaud@arnaud-laptop:~$ sudo fdisk -l

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x4824a142

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1       11620    93337618+   7  HPFS/NTFS
/dev/sda2           11621       19457    62950702+   5  Etendue
/dev/sda5           11621       19131    60332076   83  Linux
/dev/sda6           19132       19457     2618563+  82  Linux swap / Solaris



"/etc/fstab" contents result in terminal:
arnaud@arnaud-laptop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=04455341-4874-4f05-92cc-a359677d45ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=340395be-4c07-43e2-9330-a46971635d13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thank you in advance
Arnaud

---

### Post by jerome schatten on 2010-04-03
Hi Arnaud... Do you know whether your optical drive is PATA or SATA or IDE?

What does the result of '**cat /etc/mtab**' look like ?  Do you see the drive?

It's been a long time since I thought about this problem.

jerome

---

### Post by Arnaud22 on 2010-04-05
Hi Jerome,

Thanks for your message.

I'm don't really know how to find about the sata or ide thing. I put the results of list of my devices "lspci" and info about my drive (?) "hdparm -I /dev/sda" if that helps?

root@arnaud-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)


root@arnaud-laptop:~# sudo hdparm -I /dev/sda
/dev/sda:

ATA device, with non-removable media
    Model Number:       Hitachi HTS541616J9SA00                 
    Serial Number:      SB2404SJH7SSBE
    Firmware Revision:  SB4OC70P
Standards:
    Used: ATA/ATAPI-7 T13 1532D revision 1 
    Supported: 7 6 5 4 
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  312581808
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      152627 MBytes
    device size with M = 1000*1000:      160041 MBytes (160 GB)
    cache/buffer size  = 7516 KBytes (type=DualPortCache)
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Vendor, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    Recommended acoustic management value: 128, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
       *    SET_MAX security extension
            Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    Gen1 signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
            Non-Zero buffer offsets in DMA Setup FIS
            DMA Setup Auto-Activate optimization
            Device-initiated interface power management
            In-order data delivery
       *    Software settings preservation
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
    82min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000cca51fd19f45
    NAA        : 5
    IEEE OUI    : 000cca
    Unique ID    : 51fd19f45
Checksum: correct


And here's the result of the "cat /etc/mtab":
arnaud@arnaud-laptop:~$ sudo cat /etc/mtab
[sudo] password for arnaud: 
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/arnaud/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=arnaud 0 0

---

### Post by jerome schatten on 2010-04-06
Hi again...

Well, I forgot you were using a laptop, which makes it almost impossible to switch out the hardware easily.  If it were a desktop, I would just try another drive.

You said in your first post that you got an error when you tried to mount the cdrom? Can you post the error message?

The fact that the cdrom does not appear in /etc/mtab suggests that the system is not seeing it at boot time. Here's what mine looks like:

[B]orange@orange:~$ cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/orange/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=orange 0 0
/dev/sdc1 /media/4745-FE90 vfat rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
/dev/sr0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=orange 0 0
orange@orange:~$ 

[/B]You see /dev/sr0 mounted on /media/cdrom0

At bootup, everything that happens is logged to /var/log/messages. Here's a snippet from my /var/log/messages file regarding the recognition of the optical drive:

[B]Apr  6 08:07:18 orange kernel: [    3.669606] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.04 PQ: 0 ANSI: 5
Apr  6 08:07:18 orange kernel: [    3.671248] sr0: scsi3-mmc drive: 125x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  6 08:07:18 orange kernel: [    3.671251] Uniform CD-ROM driver Revision: 3.20
Apr  6 08:07:18 orange kernel: [    3.671355] sr 6:0:0:0: Attached scsi generic sg2 type 5[/B]

Take a good look at /var/log/messages  and see if you can see any reference to your optical drive. It's a big file so you'll need some patience going through it.

All the above said, if it were me, I would do a complete re-install of 9.10 and see how that goes. Obviously, the drive is capable of working or you wouldn't have been able to install in the first place.

But first, let's see the exact error message you're getting as regards the optical drive.

jerome

---

### Post by Arnaud22 on 2010-04-28
Hello Jerome,

Thanks again for your help!

Here is what i found in /var/log/messages (rebooted today so found these 2 entries):

Apr 28 13:13:56 arnaud-laptop kernel: [    3.127336] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GRS6 PQ: 0 ANSI: 5
Apr 28 13:13:56 arnaud-laptop kernel: [    3.136959] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 28 13:13:56 arnaud-laptop kernel: [    3.136965] Uniform CD-ROM driver Revision: 3.20

Apr 28 13:32:49 arnaud-laptop kernel: [    3.331527] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GRS6 PQ: 0 ANSI: 5
Apr 28 13:32:49 arnaud-laptop kernel: [    3.339145]  sda5sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 28 13:32:49 arnaud-laptop kernel: [    3.341178] Uniform CD-ROM driver Revision: 3.20

Hope that helps

Arnaud

---

### Post by jerome schatten on 2010-04-28
OK... so Ubuntu IS seeing the drive at boot up but is not automatically mounting it. In my message #32 to you a few weeks ago, I asked to see the optical drive error message  you were getting at boot up. Let's see that, OK?

I suggest you try and mount the drive manually from the command line.  In a terminal, type 'man  mount' to get the syntax. If you can't make any sense out of the man page for mount, I'll try and figure it out for you.

Maybe try another post to the group and get someone more knowledgeable than I am.

---

### Post by Arnaud22 on 2010-05-05
"the optical drive error message you were getting at boot up. Let's see that, OK?" you mean the error i get when i try to mount the cdrom (not errors i would get at computer boot up)?

-Here is the error message when i try to mount cdrom from desktop (double clicking on cd icon "cdrom0") from left hand corner ubuntu menu "places" :

special device /dev/scd0 doesn't exist

-Here is the error message when i try to mount from terminal:

arnaud@arnaud-laptop:~$ mount cdrom0
mount: ne peut repérer cdrom0 dans /etc/fstab ou /etc/mtab
(it can't locate cdrom0 in /etc/fstab ou /etc/mtab)

Looked through man mount but not sure if i'm doing the right terminal command to mount the cdrom manually.
I'm a bit confused there....

---

### Post by Arnaud22 on 2010-05-05
Looked around again and found this thread [http://www.linuxforums.org/forum/redhat-fedora-linux-help/61990-mounting-cd-rom.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/61990-mounting-cd-rom.html). I'm not sure if that would help us here but maybe you would understand better than i would if this is relevant.

Here is also an error message. I typed "less /etc/fstab" in terminal (from this thread) and had the result:
 
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
 # for a device; this may be used with UUID= as a more robust way to name
 # devices that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 # / was on /dev/sda5 during installation
 UUID=04455341-4874-4f05-92cc-a359677d45ab /               ext4    errors=remount-ro 0       1
 # swap was on /dev/sda6 during installation
 UUID=340395be-4c07-43e2-9330-a46971635d13 none            swap    sw              0       0
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
 ~
 ~
 ~
 ~
 ~
 ~
 ~
 ~
 (END) 
 
 Also, at some point they mention modifying /etc/fstab text or putting "all-generic-ide" as boot parameter in GRUB, but don't really understand what they mean so don't know if it's actually relevant to us here.

Thanks again for your help

---

### Post by jerome schatten on 2010-05-05
From your /etc/fstab:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

This means your cdrom drive IS recognized and is called 'scd0'

It seems to me it should work now.

Put it a non-audo CD, go to /mnt/cdrom0 and type 'ls' <enter>and see what happens.
If nothing go to / and type 'mount /dev/scd0' <enter>

Now if you go back to the mount point /mnt/cdrom0, if all is well, an 'ls' should show what's on the cdrom.

From what I understand, audio cd's/dvd's don't show up as mounted as they don't have a file system on them. Again, do the above with a data cd not an audio cd and tell me what happens. 

If you can see the data on the cd, and your computer won't play an audio cd, then that's a different problem than I thought you had.

For that problem you should post a new thread with a subject something like:

Ubuntu reads data cd but won't play audio cd

j.

---

### Post by Arnaud22 on 2010-05-10
hi,

I took a data cd to try this out.

I've got still the same error when trying to mount from from ubuntu menu with the mouse (special device /dev/scd0 doesn't exist)

Nothing happens when i go to /mnt/cdrom0 and type 'ls' in the terminal. (by the way, my folder in /mnt is cdrom but don't have a cdrom0 folder. I have this folder name in the ubuntu menu "places" though maybe i need to create a folder cdrom0 in /mnt?)

Again this error message (special device /dev/scd0 doesn't exist) when trying 'mount /dev/scd0 at /mnt/cdrom

---

### Post by Arnaud22 on 2010-05-17
hi
i reinstalled the ubuntu 10.04 and the CD/DVD drive was recognised at boot up. I managed to mount it aswell and access data on it. I hope that'll stay stable. Thanks for your help though!!

---

