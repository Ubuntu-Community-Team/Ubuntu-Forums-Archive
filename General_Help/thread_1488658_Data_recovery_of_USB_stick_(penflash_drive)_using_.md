---
title: "Data recovery of USB stick (pen/flash drive) using ntfs/fat fs .. physical damage?"
date: 2010-05-20
forum: General Help
---

### Post by MrPok on 2010-05-20
[[ The "General Help" forum seemed like the correct place to post this -- if not, please move ]]

Hello,

I want to recover data from a malfunctioning USB stick (or "pen drive" or "flash drive") that belongs to my girlfriend. *(omg why didn't she make backups? :shock:)*

The model is a Dane-Elec 8Gb, and had presumably a Windows FAT or NTFS file system. 
Apparently, the Windows XP machine that the drive was connected to crashed, and afterwards the os would not recognize the drive anymore (no drive letter in explorer, no luck in agreeing to check for errors and fix etc.) The people at her work plugged it in other windows machines (e.g. vista) as well, which is as I've learned unwise to do after a drive faillure. As far as I know, they did not write anything to the drive after the crash, but I can't be sure.

After googling and reading the following:
[LIST]
[*][Ubuntu Documentation > Community Documentation > DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
[*][Gentoo Forums Forum Index->Documentation, Tips & Tricks->Recovering files with "The Sleuth Kit"]("http://forums.gentoo.org/viewtopic-t-365703.html")
[*][reconstructing heavily damaged hard drives]("http://matt.matzi.org.uk/2008/07/03/reconstructing-heavily-damaged-hard-drives/")
[*][Linux LEO - The Law Enforcement and Forensic Examiner's Introduction to Linux]("http://www.linuxleo.com/")
[*]..and browsing a bit through [SourceForge.net > Projects > The Sleuth Kit > Mail > Archive]("http://sourceforge.net/mailarchive/forum.php?forum_name=sleuthkit-users&max_rows=25&style=nested&viewmonth=201005")
[/LIST]
I hope that it is either a _lost partition_ or a _damaged filesystem_ that I'm dealing with here.

[INDENT]Before doing anything with the broken drive, I started out by *trying out* the techniques (dealing with damaged filesystems) described in the links above *on an old working 256mb USB stick* I (still) had lying around.
I placed a couple of files on the 256mb USB stick and made an image of it, using **ddrescue** (that is GNU ddrescue, packaged as *gddrescue*).
Next, I tried out the programs: **Foremost**, **Scalpel**, **Testdisk** (and Photorec) and from the Sleuth Kit (TSK) **fls** (in combination with **icat**).
This all worked fine, and it was fascinating to see how much (old) removed data could still be recovered.[/INDENT]

--

[SIZE="3"]However[/SIZE], when I plug in the malfunctioning usb flash drive I am unable to retrieve anything using the above techniques.
After insertion the drive does not show up at the expected [FONT="Courier New"]/dev/sdb1[/FONT] (as was the case when I connected the properly functioning 256mb one). In fact, it doesn't show up ([FONT="Courier New"]fdisk[/FONT]) at all.

Testdisk does show that the usb flash drive is connected:
> Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 250 GB / 232 GiB - ATA FUJITSU MHZ2250B
**Disk /dev/sdb - 5632 B -  USB MEMORY BAR**

[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

Note however, that the size shown is not something in the order of 8gb, but _only 5632 B_. :-k 
In Ubuntu's system "disk utility" the usb flash drive is listed as Model "Silicon Motion, Inc. USB MEMORY BAR" and (again) with Capacity 5,632 bytes. It also states it is "Not Partioned". 

Since testdisk did give me a [FONT="Courier New"]/dev/sdb[/FONT], I thought I might as well try ddrescue, but to no avail:
> Initial status (read from logfile)
rescued:         0 B,  errsize:    5632 B,  **errors:       1**
Current status
rescued:         0 B,  errsize:    5632 B,  current rate:        0 B/s
   ipos:      5120 B,   **errors:       1**,    average rate:        0 B/s
   opos:      5120 B,     time from last successful read:       0 s
Finished  

Unfortunately, I am no expert in all of this (even though after all this reading I've learned a lot on recovery).. I hope I can somehow recover/fix/restore the partition tables, although I have a bad feeling about that small capacity...

Gparted didn't show the device, but starting it from commandline:
> $ sudo gparted
======================
libparted : 2.2
======================
**Input/output error during read on /dev/sdb**
When I run [FONT="Courier New"]parted[/FONT], I get:
> $ sudo parted /dev/sdb
GNU Parted 2.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescue                                                           
**Error: /dev/sdb: unrecognised disk label** 

After yet some more googling, I decided to do a [FONT="Courier New"]hexdump[/FONT]..
> $ sudo hexdump -Cv /dev/sdb
hexdump: /dev/sdb: **Input/output error**

I am hoping that the discussion on [-this link-]("http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1274361669876+28353475&threadId=1028066") can lead to an answer, 
[QUOTE=Matti Kurkela @ HP]There might be some old garbage data at the beginning of the disk, which could cause the geometry to be detected wrong.[/QUOTE] 

..but I don't see how to proceed in using that insight (without destroying data). Anybody?


Power spikes frying the device or disrupting its chip firmware? :(
Is there anything else I can try to save this poor piece of silicon? :(


Any help is much appreciated!

Kind regards,
p a u l

---

### Post by dino99 on 2010-05-20
with such troubles you need to rewrite the partitioning index, use

[http://partedmagic.com/](http://partedmagic.com/) features, or [http://www.cgsecurity.org/](http://www.cgsecurity.org/) tools

partedmagic can duplicate, copy, move data if it can read your device

---

### Post by MrPok on 2010-05-20
> **dino99 said:**
> with such troubles you need to rewrite the partitioning index, use

[http://partedmagic.com/](http://partedmagic.com/) features, or [http://www.cgsecurity.org/](http://www.cgsecurity.org/) tools

partedmagic can duplicate, copy, move data if it can read your device
I already tried Testdisk (and Photorec, both originating from  [http://www.cgsecurity.org](http://www.cgsecurity.org)), but I will be sure to check out the tools listed at partedmagic.com Thanks for the link! When I get some results I'll post back.

Kind regards,
p a u l

---

