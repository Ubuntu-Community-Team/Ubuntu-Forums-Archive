---
title: "DVD/CD ROM not working"
date: 2006-01-25
forum: General Help
---

### Post by jacqui1811 on 2006-01-25
Hi guys. 
I am a fairly new convert to Ubuntu (Think it's fab so far !) and a couple of weeks ago installed Breezy Badger on a machine that did have W*n*o*s 2000.
Everything has been fine for a while but last night I tried to put in a dvd that I have watched on the machine (pre Ubuntu) and nothing happened.
I actually watched the boot up today and whilst it is booting up it shows the following.
[4294705.771000] (Reserved error code--(asc=0x09,ascq=0x04)) 
The failed "read cd/dvd capacity" packet command was....
Forgive me I did not manage to get the rest.

Anyway.
tried to mount it from the command line and :
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Tried that and and got the following :
jacqui@laptop-2:/etc$ dmesg | tail
[4323693.457000] end_request: I/O error, dev hdc, sector 64
[4323693.457000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4323693.587000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4323693.587000] hdc: packet command error: error=0x40 { LastFailedSense=0x04 }
[4323693.587000] ide: failed opcode was: unknown
[4323693.596000] ATAPI device hdc:
[4323693.596000]   Error: Hardware error -- (Sense key=0x04)
[4323693.596000]   (reserved error code) -- (asc=0x09, ascq=0x04)
[4323693.596000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4323693.596000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

Anyway guys I would really appreciate some help.
Thanks.
Jacuqi.

---

### Post by dcstar on 2006-01-25
[QUOTE=jacqui1811]
.......
[4323693.596000]   Error: Hardware error -- (Sense key=0x04)
[4323693.596000]   (reserved error code) -- (asc=0x09, ascq=0x04)
[4323693.596000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4323693.596000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

Anyway guys I would really appreciate some help.
Thanks.
Jacuqi.[/QUOTE]
Possibly bad DVD or bad drive.

You may try enabling/disabling DMA for the drive, do a forum search for the detailed instructions on how this is done.

---

### Post by kingsidy on 2006-01-25
looks like a bad cd. usually, that is hen u get those hdc error. maybe too many scratches.    also make sure you have libdvdcss2

---

