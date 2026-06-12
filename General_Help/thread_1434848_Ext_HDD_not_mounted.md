---
title: "Ext HDD not mounted"
date: 2010-03-20
forum: General Help
---

### Post by malel on 2010-03-20
I did a new install of Ubuntu 9.10 yesterday but now find I am unable to mount my ext HDD which has all my backup files on it . It shows up in fdisk -l, gparted but the error message I get is that it is not in /etc/fstab. What entry do I have to make to put it in /fstab to get it auto mounting like it used to .


mal@Pentium4:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd722da6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ead3aca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38912   312560608+   7  HPFS/NTFS
mal@Pentium4:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab




I have spent many hours this morning going through a lot of threads but nothing  has been spotted to help my case .
Any help would be appreciated.

---

### Post by Roasted on 2010-03-20
You're not completing the command. You say sudo mount /dev/sdb1, but you don't have a destination. A completed mount command looks like:

sudo mount /dev/sdb1 /media/external

Assuming that the folder "external" exists in the /media directory.

I'm not in Ubuntu to show you my fstab, but I mount my drives with the UUID instead of the device ID. You can find the UUID by issuing "sudo blkid" to terminal. It'll show you the UUID (unique identifier) to each partition, and you can set it up in fstab accordingly.

If I remember right, mine is just

UUID=F82349r5839483034989 /media/storage *then defaults here*

It looks something like that... UUID=whatever-it-is, mount point, and defaults 0 0 or 0 2 or whatever is the default for fstab.

---

### Post by malel on 2010-03-20
Thank you roasted . Here is what I got


mal@Pentium4:~$ sudo mount /dev/sdb1 /media/disk
[sudo] password for mal: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and this

mal@Pentium4:~$ sudo blkid
/dev/sda1: UUID="43b5a8bc-026a-4eaa-b4d7-d4b5dc902c09" TYPE="ext4" 
/dev/sda5: UUID="d87f2432-6913-45c0-83e2-41c32384c964" TYPE="swap" 
/dev/sdb1: UUID="bef3e011-a2db-4c7f-be53-d2b8f3999da0" TYPE="ext4"

---

### Post by mechro on 2010-03-20
If you have a standard Ubuntu install then an external drive should be recognised as Removable Drives and Media and should automount without needing an fstab entry.

What happens if you unplug/replug the drive?

---

### Post by malel on 2010-03-20
Thank you Mechro . When I unplug and plug it back this is what I get


"Unable to mount 320 GB filesystem
Error mounting: mount exited with error code 32: mount:wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or code helper program, or other error
In some cases useful info is found in syslog - try dmesg ! tail or so"

I cant see syslog using dmesg because my keyboard does not have a straight up and down line key .

---

### Post by mechro on 2010-03-20
Sounds like a corrupted file system.

If you want a | you can always copy and paste it from here...

```
dmesg | tail
```

---

### Post by malel on 2010-03-20
This is what I get now


mal@Pentium4:~$ dmesg | tail
[   23.928021] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   25.340006] eth1: no IPv6 routers present
[   31.928021] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   35.630274] usb 3-1: usbfs: interface 0 claimed by usblp while 'xsane' sets config #1
[   39.916022] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   47.928033] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   55.928023] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   63.932025] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   71.936024] usb 1-8: reset high speed USB device using ehci_hcd and address 5
[   79.940044] usb 1-8: reset high speed USB device using ehci_hcd and address 5

---

### Post by mechro on 2010-03-20
OK. Your external drive has an NTFS partition on it. NTFS is a Windows file system. You could try an NTFS disk check/fix...

```
sudo ntfsfix /dev/sdb1
```

---

### Post by malel on 2010-03-21
I tried that and here is what I got :


mal@Pentium4:~$ sudo ntfsfix /dev/sdb1
[sudo] password for mal: 
sudo: ntfsfix: command not found

---

### Post by mechro on 2010-03-21
Hmm... I thought the NTFS stuff was installed in Karmic... perhaps not.

Install the package...

```
sudo apt-get install ntfsprogs
```

And retry...

```
sudo ntfsfix /dev/sdb1
```

---

### Post by vanadium on 2010-03-21
There is something strange here. Your fdisk -l output reports /dev/sdb1 as an ntfs volume. Your blkid command, though, reports the partition as an ext4 volume.

Anyway, your mount command shows that the system is not capable of automatically sorting out the file system type.

I have to agree with mechro, that this looks like a corrupted file system. Probably you will need to reformat it. Since it is a backup drive, this might be the quickest solution: reformat the partition and re-create the backup of your data.

---

### Post by malel on 2010-03-21
Thank you for your help and patience 'Mechro' . I have carried out all that but this is what I got back. I really don't know what is going on as this never happend in 9.04.

mal@Pentium4:~$ sudo ntfsfix /dev/sdb1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

---

### Post by malel on 2010-03-21
Thank you 'Vanadium' It looks like I can reformat the drive using 'gparted' but how do I save the data on the disk before reformatting

---

### Post by soltanis on 2010-03-21
Did you create your backup disk under Linux or under Windows? We need to know what kind of partition it is supposed to be.

It is reporting itself as an ext4 system, but if it is NTFS then this will cause the mount command to fail. Try

```

mount -t ntfs /dev/sdb1 /media/disk

```

If you get an error message, please immediately do

```

dmesg | tail

```

And post that here (I didn't see anything relevant in the last output you posted), thanks.

---

### Post by malel on 2010-03-21
Thank you . Here is the results


mal@Pentium4:~$ sudo mount -t ntfs /dev/sdb1 /media/disk
[sudo] password for mal: 
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mal@Pentium4:~$ dmesg | tail
[ 1823.128272] Descriptor sense data with sense descriptors (in hex):
[ 1823.128275]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1823.128288]         00 4f 00 c2 e0 50 
[ 1823.128294] sd 7:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 1823.169514] sd 7:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[ 1823.169521] Descriptor sense data with sense descriptors (in hex):
[ 1823.169523]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1823.169536]         00 4f 00 c2 e0 50 
[ 1823.169542] sd 7:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 2567.116015] usb 1-8: reset high speed USB device using ehci_hcd and address 5

---

### Post by malel on 2010-03-21
Soltanis,

It was formatted for ext4 but for some reason it has an unallocated 7.84 Mb at the end.
This was working quite happily in Ubuntu 9.04 so where would the corruption have come from . I have some pretty important docs on that HDD

---

### Post by mechro on 2010-03-22
When did you format the drive as ext4? Did you do anything with the drive when you installed 9.10?

I'm just wondering whether there was some remnant of a Windows installation on the drive which was somehow picked up by the 9.10 install.

If you're trying to recover data off the drive you could try **testdisk** which might be able to recover and rewrite a working partition table.

Either from your Ubuntu installation or a LiveCd you can install testdisk with **sudo apt-get install testdisk**. Run it with the command **sudo testdisk**. Here's some information on testdisk...

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Make sure you only work on the problem drive /dev/sdb. If you're not sure what to do you can quit the program with Ctrl+C and then do some more research or ask more questions here.

Edit... by the way, I should also wait and see if soltanis has any suggestions re your last dmesg | tail message.

---

### Post by vanadium on 2010-03-22
Since it was your backup partition, I thought you could just reformat the partition and put your backup back.

If the partition contains unique data that is not backed up, then you will have a harder time.

You could try if a 
```

sudo mount -t ext4 /dev/sdb1 /media/disk

```
does mount the drive. I don't expect so. The mount command is normally capable by its own to determine a file system. That it does not suggests serious corruption of the partition to me.

If data is to be rescued, testdisk indeed is a possiblility. But it won't be fun.

---

### Post by malel on 2010-03-22
Alright folks . I have not had the time to do anything more but to re-install 9.10 which came back with calling the ext HDD 'sbg'.
I have now removed 9.10 and re-installed 9.04 and I can get everything from the ext HDD ok. This is the second time I have had trouble with a fresh install of 9.10 so I will not touch it again . We can close this thread now.
Many thanks for your help

---

