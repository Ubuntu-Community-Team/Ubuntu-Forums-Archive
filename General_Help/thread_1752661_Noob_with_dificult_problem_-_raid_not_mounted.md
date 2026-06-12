---
title: "Noob with dificult problem - raid not mounted"
date: 2011-05-08
forum: General Help
---

### Post by bpgoa on 2011-05-08
Help.

I am a Linux Noob - there I said it out loud.

I have v 10.10 running the following (and I still have no idea how i got this all working)

Myth, Squeeze server, X10 control system for the house,Virtualbox (where i run some windows stuff) and a general file and print service.

it has 5 disk drives attached 

1 - system disk
5- external usb to back up data to
2,3,4 - 2 tb drives in a raid config



****   I just re started the server and the raid volume has not mounted *****

I looked in the webmin interface and the device is there but it doesn't seem to have the partitions attached.  again in webmin, the partitions seem to be on each of the drives.

I used crash-plan to back up the data and music, but not the video, so I would prefer not to have to rebuild the lot if I don't have to ...  I really don't want to re build the lot out of my lack of experience with Linux.   

Is there an easy (ish) way of putting the raid back together to see if it's just dropped its config...  and the data is in tact (or can be rebuild from two of the three drives.

be gentle with me...  


Ade.

---

### Post by bpgoa on 2011-05-08
ok... looked around on other threads and (blindly) used the command ...

 
mdadm --assemble --force --scan /dev/md0 
to try and force the partition up..

I then could mount the drive in wemin..  and got 

**RAID device options**     **Device file** /dev/md0   [SIZE=2]RAID level[/SIZE] [SIZE=2]Redundant (RAID5)[/SIZE]   [SIZE=2]Filesystem status[/SIZE] [SIZE=2]Mounted on /mnt[/SIZE]   [SIZE=2]Usable size[/SIZE] [SIZE=2]3907023872 blocks (3.64  TB)[/SIZE]   [SIZE=2]Persistent superblock?[/SIZE] [SIZE=2]Yes[/SIZE]   [SIZE=2]Layout[/SIZE] [SIZE=2]Default[/SIZE]   [SIZE=2]Chunk size[/SIZE] [SIZE=2]4 kB[/SIZE]   [SIZE=2]RAID errors[/SIZE] [SIZE=2][COLOR=#ff0000]1  disks have failed[/COLOR][/SIZE]   [SIZE=2]RAID status[/SIZE] [SIZE=2]clean, degraded[/SIZE]   [SIZE=2]Partitions in RAID[/SIZE] [SIZE=2]SATA device C partition 1 
SATA device D partition 1 [/SIZE]


Again using Webmin....  (noob).... i looked at the partitions on the disk....   

[SIZE=2]SATA device E partition 1[/SIZE] seems to be missing


again using Webmin I get this for E...  

[SIZE=+2]Edit Partition[/SIZE] 
SATA device E
     **Partition Details**         **Location** SCSI device E partition 1 **Device file** /dev/sde1   **Type**  AIX AIX bootable AST Windows swapfile Amoeba Amoeba BBT BBT BSD/386 BSDI filesystem BSDI swap BeOS CP/M CP/M / CTOS Compaq diagnostic DOS access DOS read-only DOS secondary DRDOS/sec FAT12 DRDOS/sec FAT16 DRDOS/sec FAT16 <32M DiskSecure Multi-Boot EZ-Drive Empty FAT12 FAT16 FAT16 <32M GNU HURD or SysV Golden Bow Hidden FAT12 Hidden FAT16 Hidden FAT16 < 32M Hidden NTFS Hidden Windows FAT (1b) Hidden Windows FAT (1c) Hidden Windows FAT (1e) IBM Thinkpad hibernation LANstep Linux Linux LVM Linux RAID Linux extended Linux swap Minix / Old Linux / Solaris NEC DOS NTFS NTFS volume set (86) NTFS volume set (87) NeXTSTEP Novell Netware 286 Novell Netware 386 OPUS OS/2 boot manager OS/2 hidden C: drive Old Minix OnTrack DM OnTrack DM6 OnTrack DM6 Aux1 OnTrack DM6 Aux3 OpenBSD PC/IX PPC PReP boot PartitionMagic recovery Priam Edisk QNX 4.x QNX 4.x 2nd partition QNX 4.x 3rd partition SFS SpeedStor SpeedStor SpeedStor SpeedStor large partition Syrinx Venix 80286 Windows FAT16 LBA Windows FAT32 Windows FAT32 LBA XENIX root XENIX usr   **Extent** 1 - 243201 of 243201   **Status** Not in use **Size** 1.82 TB                    Old Linux Native Linux Native New Linux Native MS-DOS Windows Minix   Builds a new  filesystem of the selected type on this partition, permanently erasing  any existing files. You must do this after creating a new partition or  changing an existing one.     [[IMG]https://192.168.1.100:10000/images/left.gif[/IMG]]("https://192.168.1.100:10000/fdisk/index.cgi")  [Return to disk  list]("https://192.168.1.100:10000/fdisk/index.cgi") 


And when i look at the   mdadm.conf

DEVICE /dev/sda1 /dev/sdc1
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 level=raid5 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1

No Sign of   /dev/sde1 


Where next ?  


has my drive failed?

Should i try to re partition  /dev/sde1 and add it back into the array?


the array seems in tact...   mounted and all ok...

---

### Post by bpgoa on 2011-05-08
Panic over....

told you I was a noob.....


switch of external USB...
re boot....

all comes up OK.....



so ... the question changes...  how do i ensure that the external USB drive comes up as SDE1!!!!

---

### Post by Anonymous is Incognito on 2011-05-08
Looking at the webmin output, you can say that your hard-drive *has* failed. You can also run

```
mdadm -D /dev/sd0
```

as root, to get a more detailed output. If you do, please post it.

With RAID5 one drive can fail, that is the reason all is still working. I'd replace it.

When you put a new one in, mdadm will automatically sync it with the rest of the array. At that point you are 'safe' again.

The USB drive should show up as
```
/dev/sde
```
you should edit the [FONT="Courier New"]/etc/fstab[/FONT] file according to your needs.

---

### Post by bpgoa on 2011-05-08
it was the external USB drive moving the order of the naming of the devices...

now need to work out how to force the USB to something else ...

---

