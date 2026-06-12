---
title: "Error: No such partition entering rescue mode"
date: 2012-01-08
forum: General Help
---

### Post by linuxnovice. on 2012-01-08
Well I was having some problems with my computer, the fan was failing and it kept randomly shutting off but I kept using it until one day it shut down and when I tried using it I got this error message

> Error: no such partition entering rescue mode

nevertheless I needed some important files so I burned a SLAX live cd to access my files, but the only storage media slax detects is the floppy disk, I have tried accessing my files with other live distros but the same thing happens. 

Seems like my computer isn't detecting my HD, what might be going on.


This is the error message I try using dmesg from the terminal 

> Buffer I/O error on device hda1, logical block 343
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=2392, sector=2392
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=2392, sector=2392
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=2392, sector=2392
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=2392, sector=2392
ide: failed opcode was: unknown
ide0: reset: success
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2392, sector=2392
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2392
Buffer I/O error on device hda1, logical block 344
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=2393, sector=2393
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2393, sector=2393
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2393
Buffer I/O error on device hda1, logical block 345
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=2394, sector=2394
ide: failed opcode was: unknown



what might be going on please help!

---

### Post by carl4926 on 2012-01-08
Sounds like a dead HD

---

### Post by linuxnovice. on 2012-01-08
> **carl4926 said:**
> Sounds like a dead HD

what can I do about it is there a way to get my information back

---

### Post by carl4926 on 2012-01-08
From the live CD you are using
Open a terminal. Do you get any info when you do

```
su -
fdisk -l
```

---

### Post by linuxnovice. on 2012-01-08
> **carl4926 said:**
> From the live CD you are using
Open a terminal. Do you get any info when you do

```
su -
fdisk -l
```


I get no output 


grub still loads, does that mean that part of my hard drive is still alive? can I try to manually mount my HD or something 

Thanks!

---

### Post by carl4926 on 2012-01-08
Well. That's not good.

I'm no expert in this area. So I suggest you wait for better advices. But IIRC, it's better not to try accessing the partitions until we have established clearly the problem and a plan of action (if any).

I understand 'TestDisk' can help in recovering data. But not sure if it applies to your situation.

One thing you should check is that the HD SATA and Power cables are connected OK
You would power off
Then just pull and re-seat the connectors. Make sure they are good. Both on the HD and the Mobo

---

### Post by linuxnovice. on 2012-01-08
> **carl4926 said:**
> Well. That's not good.

I'm no expert in this area. So I suggest you wait for better advices. But IIRC, it's better not to try accessing the partitions until we have established clearly the problem and a plan of action (if any).

I understand 'TestDisk' can help in recovering data. But not sure if it applies to your situation.

One thing you should check is that the HD SATA and Power cables are connected OK
You would power off
Then just pull and re-seat the connectors. Make sure they are good. Both on the HD and the Mobo


Thanks for your help!
I will check if every cable is connected 

btw I waited some minutes but I got this output from fdisk

> Unable to read /dev/hda


---

### Post by carl4926 on 2012-01-08
/dev/hda

suggests to me, your HD's are not SATA but the old PATA, big flat ribbon type cable

You didn't say if it was a Laptop or PC

---

### Post by topsites on 2012-01-08
The only method I know of that stands a chance of working and with no guarantees of success...
Is to hook up a working drive as master, and the one you suspect to be faulty as slave.
Then try and access it from within the File Manager because the first thing you need is a computer that boots, you can not access anything while it's not even booting.

Via this method you can almost always salvage some of it, and almost never all of it, as to how much, that all depends but anywhere from a few files to almost the whole dang drive.

Unfortunately, and in most cases the two drives will need to be of the same hardware type (i.e.:  EIDE - EIDE or SATA-SATA etc) if one is IDE and the other SATA your chances are slim to none.

It's easy enough when the broken one is of the late technology (SATA) or also sometimes you can scare up a cheap used IDE on EBAY.
As to whether I would spring the cash for a drive just for that purpose is another story.

---

### Post by linuxnovice. on 2012-01-08
> **carl4926 said:**
> /dev/hda

suggests to me, your HD's are not SATA but the old PATA, big flat ribbon type cable

You didn't say if it was a Laptop or PC

yeah it has the big flat ribbon type cable

> **topsites said:**
> The only method I know of that stands a chance of working and with no guarantees of success...
Is to hook up a working drive as master, and the one you suspect to be faulty as slave.
Then try and access it from within the File Manager because the first  thing you need is a computer that boots, you can not access anything  while it's not even booting.

Via this method you can almost always salvage some of it, and almost  never all of it, as to how much, that all depends but anywhere from a  few files to almost the whole dang drive.

Unfortunately, and in most cases the two drives will need to be of the  same hardware type (i.e.:  EIDE - EIDE or SATA-SATA etc) if one is IDE  and the other SATA your chances are slim to none.

It's easy enough when the broken one is of the late technology (SATA) or  also sometimes you can scare up a cheap used IDE on EBAY.
As to whether I would spring the cash for a drive just for that purpose is another story.

that sounds very complicated, but I will try it because I need my files

---

### Post by carl4926 on 2012-01-09
> **topsites said:**
> The only method I know of that stands a chance of working and with no guarantees of success...
Is to hook up a working drive as master, and the one you suspect to be faulty as slave.
Then try and access it from within the File Manager because the first thing you need is a computer that boots, you can not access anything while it's not even booting.

Via this method you can almost always salvage some of it, and almost never all of it, as to how much, that all depends but anywhere from a few files to almost the whole dang drive.

Unfortunately, and in most cases the two drives will need to be of the same hardware type (i.e.:  EIDE - EIDE or SATA-SATA etc) if one is IDE and the other SATA your chances are slim to none.

It's easy enough when the broken one is of the late technology (SATA) or also sometimes you can scare up a cheap used IDE on EBAY.
As to whether I would spring the cash for a drive just for that purpose is another story.

But the OP already tried accessing it from a Live CD
Which is exactly the same principle you are describing. Except in such a way as to confuse.

---

