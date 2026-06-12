---
title: "Retrieving files from a corrupted USB stick"
date: 2011-12-10
forum: General Help
---

### Post by Walmit on 2011-12-10
Dear all,

I am currently trying to retrieve files from a corrupted USB mass storage stick and I could use some help.

Let’s me explain the issue. When I plug the USB stick into a Windows or Linux PC, the key is detected as not formated while I am sure this was the case case previously.

On Ubuntu, in the /dev directory on Linux, I can see the /dev/sdb file but no /dev/sdb1 entry. When I tried to mount manually the device via the following command “"sudo mount -t vfat /dev/sdb /media/", I got the following message:
> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
 missing codepage or helper program, or other error
 In some cases useful info is found in syslog - try
 dmesg | tail  or so
The output of dmesg mentions:
> [ 2530.652525] FAT: bogus logical sector size 65535
[ 2530.652533] VFS: Can't find a valid FAT filesystem on dev sdb

I have copied the whole memory image of the USB stick via dd (sudo dd if=/dev/sdb of=sdb.image) in order to examine it with GHex editor and it indeed appears that the 1st sector of the stick is erased and replaced by “0xFF” bytes (this explains why the OS was not able to mount it automatically). However, the remaining part of the image seems intact.

So my question is the following: could you recommend me some good software to recover the files from the memory image?

Thanks in advance for any help.

Best regards

---

### Post by Walmit on 2011-12-10
By "googling" a little, I found the Photorec software ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)). 
That was all what I needed and I have been able to recover my files.

For any interested reader, have a look at the following post on a Gentoo forum: [http://www.mail-archive.com/gentoo-user@lists.gentoo.org/msg55653.html](http://www.mail-archive.com/gentoo-user@lists.gentoo.org/msg55653.html). This helps me a lot.

---

### Post by grey1beard on 2011-12-23
Walmit, I have a similar problem, but not identical.
My usb stick is recognised as present if I use lsusb, and in the file browser, within the /dev directory an sdb file is shown when I plug in the usb stick.

However it does have a cross across the file icon (not sure what that indicates) and if I try to mount it using "sudo mount -t vfat /dev/sdb /media/", I get a message
"mount: no medium found on /dev/sdb".

Is either TestDisk or PhotoRec likely to help in this situation ?

Regards
John

---

### Post by West201 on 2011-12-25
install testdisk and then run "photorec" on the terminal. Enter your sudo password and then follow photorec's instructions.

---

### Post by grey1beard on 2011-12-25
Thanks jessejj89. I took your advice, but unfortunately photorec didn't detect the stick, only my hdd.

I presume from this that this is not a way forward for me ?

Regards
John

---

### Post by fdrake on 2011-12-25
post output of :
```
sudo apt-get install parted
sudo parted -l 
```

---

### Post by grey1beard on 2011-12-25
> **fdrake said:**
> post output of :
```
sudo apt-get install parted
sudo parted -l 
```


> john@frizzy:~$ sudo parted -l
Model: ATA HITACHI_DK23FA-3 (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  28.7GB  28.7GB  primary   ext3            boot
 2      28.7GB  30.0GB  1283MB  extended
 5      28.7GB  30.0GB  1283MB  logical   linux-swap(v1)

Why aren't you enjoying the holiday ?  ;)

Regards
John

---

### Post by fdrake on 2011-12-25
> **grey1beard said:**
> Why aren't you enjoying the holiday ?  ;)

Regards
John

i am .. ;D
do you have problem only with this one or others too:
```

sudo apt-get install lshw
lsusb && lspci | grep USB
sudo lshw -c disk -c volume

```

---

### Post by grey1beard on 2011-12-25
> john@frizzy:~$ lsusb && lspci | grep USB
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:1234 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)

> john@frizzy:~$ sudo lshw -c disk -c volume
  *-disk                  
       description: ATA Disk
       product: HITACHI_DK23FA-3
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 00M6
       serial: 1ZW564
       size: 27GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=8f3ae29e
     *-volume:0
          description: EXT3 volume
          vendor: Linux
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          logical name: /
          version: 1.0
          serial: 0bd3cf5d-fcaa-412e-8150-cc32b4f75cad
          size: 26GiB
          capacity: 26GiB
          capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
          configuration: created=2011-06-16 20:58:23 filesystem=ext3 modified=2011-12-24 00:03:39 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2011-12-25 21:05:58 state=mounted
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 1223MiB
          capacity: 1223MiB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1223MiB
             capabilities: nofs
  *-cdrom
       description: DVD reader
       product: DVD-ROM SD-R2412
       vendor: TOSHIBA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1015
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb

I've used the Quote tags - should I have used the Wrap Code tags for these large quotes ? Still a newbie.

John

---

### Post by grey1beard on 2011-12-25
Just re-read your post, and realise I'm stumbling blindly on.
No, I don't have any probs with any other usb sticks etc.
Getting late here, and pills and bedtime approach !!

John

---

### Post by fdrake on 2011-12-25
11:37pm - I hear you
well I can say only this:
i don't think you'll be able to retrieve the data (at leas not with a normal software using the USB port). My opinion is that something got damaged (hardware). I would try to see if you can reformat it with windows, but I would still be very cautious in trusting it for important file.

Hope someone else has a better solution... Good Night! :}

---

### Post by grey1beard on 2011-12-25
Thanks for your help, and a peaceful and hopefully prosperous New Year to you and yours.
John

---

### Post by fdrake on 2011-12-25
> **grey1beard said:**
> Thanks for your help, and a peaceful and hopefully prosperous New Year to you and yours.
John

Thanks , same to you and your family!

---

### Post by killermist on 2011-12-26
> **grey1beard said:**
> However it does have a cross across the file icon (not sure what that indicates) and if I try to mount it using "sudo mount -t vfat /dev/sdb /media/", I get a message
"mount: no medium found on /dev/sdb".

/dev/sdb is the "root" device which has the partition table and all the partitions on it.  Typically, unless you intentionally formatted the whole device as a filesystem instead of creating one partition for the whole device and then formatting the partition as a filesystem, you won't be able to mount the device/root.
If it isn't detecting /dev/sdb1 (the first, and probably only, partition),  then it would indicate that the actual partition table has been zeroed or otherwise damaged.  On a thumb/flash drive, /dev/sdb1 would be what you would mount.

I'm not sure how to recover from a trampled partition table.  The first should probably be to take a snapshot of the full content of the drive with dd, and then try recovery methods.

---

### Post by grey1beard on 2011-12-27
> **killermist said:**
> ..........If it isn't detecting /dev/sdb1 (the first, and probably only, partition),  then it would indicate that the actual partition table has been zeroed or otherwise damaged.  On a thumb/flash drive, /dev/sdb1 would be what you would mount.

I'm not sure how to recover from a trampled partition table.  The first should probably be to take a snapshot of the full content of the drive with dd, and then try recovery methods.

Thanks killermist, now I have the phrase I couldn't remember - "partition table".

dd ? 
Could you expand this, and is it possible to interact with the drive if the computer is only aware of the it as described above, ie in Terminal/lsusb,
> Bus 001 Device 002: ID 058f:1234 Alcor Micro Corp. Flash Drive
and as an icon in Places/Computer where it is captioned Generic USB Flash Disk  ?

Regards
John

---

### Post by killermist on 2011-12-28
Many tools anticipate some (fairly reasonable) default conditions (like "I'm working on a partition of a drive" for mkfs.[almost everything]) but have options for dealing with "fringe case" incidents like trying to recover data from a copy of a partition (if not the whole device) from a full saved-as-file copy of the whole device.

How to check/recover data from a partition from a disk/device backup without using some form of emulation/virtualization, I'm not precisely sure, but I know there are ways.  Possibly mounting the device/file copy as a loop device, then using the "partitions" of the loop device (but again, I'm not quite sure how to reference them... sadly)

[edit]
If the disk having problems (that you want to backup, to later try recovery on) is /dev/sdb, and /home/youruser is writable with enough space for the entire drive /dev/sdb 's whole area (like 16Gb for a 16Gb chip) then:
```
sudo dd if=/dev/sdb of=/home/youruser/copy-of-sdb.raw
```
[note!] Since [root] probably needed access to copy the device, sudo was used, so /home/youruser/copy-of-sdb.raw is probably owned by root.

---

### Post by grey1beard on 2011-12-29
Thanks killermist. When I return from the weekly "survival shopping", I'll get the brain in gear and start concentrating.
John
Quickly tried the code, but dev/sdb doesn't detect the stick.

---

### Post by killermist on 2011-12-30
The drive may have changed locations (virtually, if not physically), so it may be sdc, sdd, sde, etc.

Back to the title of the thread, what happened to cause the "corruption" of the usb stick?

---

### Post by grey1beard on 2011-12-30
In the dev/ folder I find sda1 - 5 and sdb, but all with a X across the icon, and 0 bytes block device.
The only othe sign of its existence that I can find is in Places/Computer/generic USB flash device, which if I right click/safely remove the icon vanishes and the stick led goes out. I f I now remove the drive, the above references all disappear.

Re original "corruption" - my only idea is I probably removed it "unsafely" from a windows partition on my desktop.
I've tried re-inserting it and Safely remove from windows, and a similar story there. It's existence on xp is nominal, and I cant open it.
I used to have no problems going back and forth with this stick between four systems, 1 xp and 3 ubuntu, and I have no problems with other sticks, just this one.

Regards
John

---

### Post by grey1beard on 2011-12-30
just done a search for sdb in the file system, and have attached a screen shot of a folder.

Is this helpful ?

John

---

