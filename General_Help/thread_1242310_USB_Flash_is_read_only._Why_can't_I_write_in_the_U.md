---
title: "USB Flash is read only. Why can't I write in the USB Flash memory?"
date: 2009-08-17
forum: General Help
---

### Post by tomasrey88 on 2009-08-17
In the computer file system, I clicked on "media", then on "disk", I right mouse click and choose "properties". Under the "permissions" tab, under "file access", I change "---" to "Read and Write". Summary; Owner = myname, Folder Access = Create and Delte Files, File Access = "Read and Write". 

However, the changes never stick. When I try to write in the folder, it would say, "Error while copying to "folder". Destination is "Read-only". 

In desperation, I've already reformatted this USB flash memory with gparted, but after I reformatted, it would allow me to put files on there, but I cannot add any additional files into the folders that I put in it. 

My external hard drive that's formatted with Windows works fine, but this USB flash memory that I reformatted with Gparted in Linux does not work at all. It is FAT32. 

Now, here's what's really funny. When I click towards the Usb Flash from the file system, it gives the info above. However, if I were to click directly on the Usb Flash drive from the desktop display, the properties tab lists, "The permissions of "disk" could not be determined. 

What should I do? I mean, I shouldn't have to delete the entire freaking USB flash every time I want to rewrite on it beyond the initial write, right? That would suck. Maybe I should reformat it with Windows? I would hate to do that. Please advise. 

The Volume tab under Properties gives;
Label:
Size: 29.8 GB
Media: Removable Hard Disk
UUID: 4A7B-049D
File System: vfat (FAT32)

Thanks,
:P

---

### Post by tomasrey88 on 2009-08-17
Please help me with this problem. Other people also have this same problem: [http://ubuntuforums.org/showthread.php?t=1240138&highlight=usb+flash](http://ubuntuforums.org/showthread.php?t=1240138&highlight=usb+flash) but it wasn't fixed for him either. 

I am using a USB 1.0 computer with a USB 1.0 hub, but with a USB 2.0 Flash memory device: Kingston Datatraveler 32 GB. 

Thanks, 
:P

---

### Post by Bradj47 on 2009-08-17
I'm also having problems with this: [http://ubuntuforums.org/showthread.php?t=1242646](http://ubuntuforums.org/showthread.php?t=1242646)

I'm trying to create a DSL boot disk and this suddenly comes up making it so I can't. I really need this disk by tomorrow.

---

### Post by tomasrey88 on 2009-08-17
Try this following diagnostic command and post it so that someone more knowledgeable may tell you what's wrong. Here is what happens when I type in the command: 

dmesg | more

  36.145577] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[   36.145904] usb usb2: configuration #1 chosen from 1 choice
[   36.145989] hub 2-0:1.0: USB hub found
[   36.146008] hub 2-0:1.0: 2 ports detected
[   36.308404] Floppy drive(s): fd0 is 1.44M
[   36.338449] FDC 0 is a post-1991 82077
[   36.353953] pata_via 0000:00:07.1: version 0.3.3
[   36.373004] scsi0 : pata_via
[   36.375512] scsi1 : pata_via
[   36.375659] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[   36.375668] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[   36.393004] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   36.537617] ata1.00: ATA-5: Maxtor 92041U4, FA520S60, max UDMA/66
[   36.537631] ata1.00: 40020624 sectors, multi 16: LBA 
[   36.551595] usb 1-1: configuration #1 chosen from 1 choice
[   36.553452] hub 1-1:1.0: USB hub found
[   36.553528] ata1.00: configured for UDMA/66
[   36.555374] hub 1-1:1.0: 7 ports detected
[   37.149356] ata2.00: ATAPI: CR-4804TE, 2.6C, max MWDMA1
[   37.149422] ata2.01: ATAPI: IDE/ATAPI CD-ROM 50XS, 196A, max UDMA/33
[   37.321132] ata2.00: configured for MWDMA1
[   37.493056] ata2.01: configured for UDMA/33
 [ 1590.488589] usb 1-1.3: new full speed USB device using uhci_hcd and address 3
[ 1590.625778] usb 1-1.3: configuration #1 chosen from 1 choice
[ 1590.930434] usbcore: registered new interface driver libusual
[ 1591.106097] Initializing USB Mass Storage driver...
[ 1591.114878] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1591.123123] usbcore: registered new interface driver usb-storage
[ 1591.123771] USB Mass Storage support registered.
[ 1591.124574] usb-storage: device found at 3
[ 1591.124586] usb-storage: waiting for device to settle before scanning
[ 1596.122783] usb-storage: device scan complete
[ 1596.126790] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler G2  1.00 PQ
: 0 ANSI: 2
[ 1596.148646] sd 2:0:0:0: [sdb] 62483464 512-byte hardware sectors (31992 MB)
[ 1596.151621] sd 2:0:0:0: [sdb] Write Protect is off
[ 1596.151645] sd 2:0:0:0: [sdb] Mode Sense: 16 24 09 51
[ 1596.151655] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1596.164106] sd 2:0:0:0: [sdb] 62483464 512-byte hardware sectors (31992 MB)
[ 1596.166609] sd 2:0:0:0: [sdb] Write Protect is off
[ 1596.166629] sd 2:0:0:0: [sdb] Mode Sense: 16 24 09 51
[ 1596.166638] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1596.166672]  sdb: sdb1
[ 1596.173558] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1596.173756] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 1609.389695] FAT: Filesystem panic (dev sdb1)
[ 1609.389745]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1609.389758]     File system has been set read-only

---

### Post by Sidewinder1 on 2009-08-17
Not sure that this will work for you but it's worked with my 4 external hard drives:
```
sudo chown -R yourloginname:yourloginname /media/disk
```
The "R" is case sensitive. That's assuming that the mount point of your flash drive is "media/disk". If not, input the proper mount point.
One of the things I don't like about all of the versions after Gutsy Gibbon is the "Permissions could not be determined" when you click on 'properties---->permissions'.
HTH, 
Side

---

### Post by Sidewinder1 on 2009-08-17
The only other thing that I can think of at the moment; did you "safely remove hardware" the last time the flash drive was mounted in winbloze? I ask this 'cause I think you said it was formatted fat32, keep in mind fat 32 has a 4 gig per file limitation...Not that that is necessarily a problem in and of itself. :-)

---

### Post by tomasrey88 on 2009-08-17
I formatted fat32 with the ubuntu live cd's gparted program. I did not use winbloz.

---

### Post by Bradj47 on 2009-08-17
That worked for me:
```

brad@rockstar:~$ sudo chown -R brad:brad /dev/sdc
brad@rockstar:~$ sudo cat /usr/lib/syslinux/mbr.bin > /dev/sdc
brad@rockstar:~$ 

```
Thanks!

---

### Post by tomasrey88 on 2009-08-17
I don't have a syslinux folder under /usr/lib/ in my hard drive. I even clicked on "show hidden files".  Why am I making mbr.bin my Usb flash drive (your /dev/sdc is my /media/disk/ ) ? I don't understand. 

Thanks,
:P

> **Bradj47 said:**
> That worked for me:
```

brad@rockstar:~$ sudo chown -R brad:brad /dev/sdc
brad@rockstar:~$ sudo cat /usr/lib/syslinux/mbr.bin > /dev/sdc
brad@rockstar:~$ 

```Thanks!

---

### Post by tomasrey88 on 2009-08-17
Right mouse click on the USB Flash icon in the desktop yields under "volume" tab;
Mount point: /media/disk
File System: vfat
Mount Options: ro nosuid nodev relative uid=1000 fmask=0077dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8

Then, under "settings", It allows you to change the mount point, file system, and mount options. What do I type in to make the "mount options" include read and write to files & create and delete folders? Please advise.

Under "permissions" tab it says "The permissions of "disk" could not be determined."
Right mouse click on the USB Flash icon in the desktop yields under "volume" tab;
Mount point: /media/disk
File System: vfat
Mount Options: ro nosuid nodev relative uid=1000 fmask=0077dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8
Then, under "settings", It allows you to change the mount point, file system, and mount options. What do I type in to make the "mount options" include read and write to files & create and delete folders? Please advise. 

I used 
panda@pandamonium:~$ sudo chown -R panda: panda /media/disk

but I had not used the following because I do not have a syslinux folder.

panda@pandamonium:~$ sudo cat /usr/lib/syslinux/mbr.bin > /media/disk


It did not work for me. Please advise.

Thanks,
:P

P.S. If I type without spaces : panda, it prints a happy face here. I tried to type above without improperly placed spaces:
panda@pandamonium:~$ sudo chown -R panda: panda /media/disk
panda@pandamonium:~$ sudo chown -R panda:panda /media/disk

---

### Post by michy99 on 2009-08-17
Try ```
sudo chmod 777 /media/disk
```

---

### Post by tomasrey88 on 2009-08-17
Didn't work. Here's the screen printout:

panda@pandamonium:~$ sudo chmod 777 /media/disk
chmod: changing permissions of `/media/disk': Read-only file system

---

### Post by oldos2er on 2009-08-17
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Sidewinder1 on 2009-08-17
panda@pandamonium:~$ sudo chown -R panda: panda /media/disk
 The "space" after the : and before the "p" in panda is wrong. Please retry and let us know; yes, I know it can be frustrating at times, :-)
Side
Copy and paste:
```
sudo chown -R panda:panda /media/disk
```Again, that's assuming that under the flash drive's Properties---->Volumes tab, the mount point is listed as /media/disk
If that doesn't work, you can try the above with panda:pandamonium or perhaps pandamonium:panda
Don't depend on the permissions tab of the flash drive. It's **always** going to say "Permissions of the "disk" could not be determined, even if the command worked.
You must try to write/save/modify to test each step **before** trying the next step.

---

### Post by michy99 on 2009-08-17
> **Sidewinder1 said:**
> panda@pandamonium:~$ sudo chown -R panda: panda /media/disk
 The "space" after the : and before the "p" in panda is wrong. Please retry and let us know; yes, I know it can be frustrating at times, :-)
Side
Copy and paste:
```
sudo chown -R panda:panda /media/disk
```
Again, that's assuming that under the flash drive's Properties---->Volumes tab, the mount point is listed as /media/disk

If you will read, you will see he left the space in the post so the : p wouldn't turn into :p, which it will if you don't put it in a code box.

---

### Post by tomasrey88 on 2009-08-17
Oldos2er: It is already mounted because I can read from it and I can unmount it after reading the data. 

**O.K. Ubuntu uberusers, I invite you to blind me with your brilliance. Please tell me how to fix it so that my usb flash can be written on as it is now read only**.

Michy99: I am a newby. How do I use a codebox? Thanks.

Thanks,
:P

---

### Post by oldos2er on 2009-08-17
Permissions on a FAT32 partition must be set when it's first mounted, since otherwise FAT32 doesn't support 'nix file permissions. You might want something like
```
mount /dev/sdb1 /media/data2 vfat defaults,user,dmask=000,fmask=111
```
for example

---

### Post by michy99 on 2009-08-17
First, the easy question. To put text in a code box, select the text and click on the # at the top of the reply box. Or you can do it manually by putting [ code ] at the beginning and [ /code ] at the end, without the spaces.

As to the flash drive question, I'll be back in a little bit with a suggestion.

---

### Post by cariboo on 2009-08-17
Have you tried:

```
sudo chmod -R 777 /media/device
```

BTW the smilie your were getting is because you typed [noparse]:p[/noparse].
To disable smilies in text use the advanced editor, and scroll down and put a check-mark beside disable smilies in text.

---

### Post by Sidewinder1 on 2009-08-17
> **michy99 said:**
> If you will read, you will see he left the space in the post so the : p wouldn't turn into :p, which it will if you don't put it in a code box.

A thousand pardons...

---

### Post by egalvan on 2009-08-17
> **cariboo907 said:**
> Have you tried:

```
sudo chmod -R 777 /media/device
```


The OP stated that the flash was FAT32...

will chmod work on this?

---

### Post by Bradj47 on 2009-08-17
> **tomasrey88 said:**
> I don't have a syslinux folder under /usr/lib/ in my hard drive. I even clicked on "show hidden files".  Why am I making mbr.bin my Usb flash drive (your /dev/sdc is my /media/disk/ ) ? I don't understand. 

Thanks,
:P

You aren't. That was what I was trying to do with my flash drive to install Damn Small Linux on it when I got the permission denied error. I was just showing that this time it didn't give me a permission denied error.

---

### Post by cariboo on 2009-08-17
All the command I gave does is make the mount point world read/writable, it has nothing to do with how it is formatted. In some cases you may have to unmount then mount the device in order for the permissions to take affect.

---

### Post by egalvan on 2009-08-17
> **cariboo907 said:**
> All the command I gave does is make the mount point world read/writable, it has nothing to do with how it is formatted. In some cases you may have to unmount then mount the device in order for the permissions to take affect.

OK, Thanks!

---

### Post by tomasrey88 on 2009-08-23
> **cariboo907 said:**
> Have you tried:

```
sudo chmod -R 777 /media/device
```BTW the smilie your were getting is because you typed [noparse]:p[/noparse]

**I just tried that but all I got was a reply stating that it is a read-only file system:**

sudo chmod -R 777 /media/disk

chmod: changing permissions of `/media/disk/Tunes/Roswell/Good Charlotte - Complicated.mp3': Read-only file system
chmod: changing permissions of `/media/disk/Tunes/Roswell/Grassy Knoll - Safe.mp3': Read-only file system

Any ideas, guys?

---

### Post by tomasrey88 on 2009-08-23
panda@pandamonium:~$ sudo mount /dev/sdb1 media/disk vfat defaults,panda,dmask=000,fmask=111
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab mtomasrey88ay be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount commantomasrey88d
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by osoviajero on 2010-08-21
> **cariboo907 said:**
> Have you tried:

```
sudo chmod -R 777 /media/device
```

BTW the smilie your were getting is because you typed [noparse]:p[/noparse].
To disable smilies in text use the advanced editor, and scroll down and put a check-mark beside disable smilies in text.

This problem is driving me crazy. I had it working up until the 10.04 upgrade, and since then CANNOT write to MP4 player. HELP.

---

