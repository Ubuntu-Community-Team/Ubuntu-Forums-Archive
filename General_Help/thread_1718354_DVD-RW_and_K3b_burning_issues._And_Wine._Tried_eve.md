---
title: "DVD-RW and K3b burning issues. And Wine. Tried everything I know to."
date: 2011-03-31
forum: General Help
---

### Post by Baniita on 2011-03-31
Brasero hates me. GnomeBaker is derpy. K3b... /Facepalm. I've checked out other threads, but they only confuse me since I'm lost in total nubbery. I don't even know how to use the terminal.
_**I RAMBLE A LOT. So I bolded/underlined stuff that goes straight to the point.**_ Sort of.

**No, I know next to NOTHING about programming.**  Seriously. I'm all  like, 'durrr'. The terminal makes me prone to the  usage of pointy and  jabby things. Long story as to why I'm using ubuntu  in the first place.  /Bashes head.

**Yes, I HAVE looked in other threads.**  But it's all jargon to me.  Or otherwise completely useless. I've  downloaded so many things now and  fffff. Here I am trying to get  cdrtools to work and I don't even know  where to start.

***I'M SERIOUSLY GOING TO RIP SOMETHING APART.*** Yes, I did take my anxiety pills, kthx. (150mg Sertraline or something. FYI.)
[U][B]
This is what K3b has to say for itself:[/B][/U]
"Writing DVD-RW in restricted overwrite mode.
Using Wodim 1.1.10 - Copyblahblahunimportantstuff...
Starting Restricted Overwrite writing at 2x speed... (My DVD-RW is x4)
X Unable to open new session.
X Probably a problem with the medium.
[B]
K3b debugging output:[/B]
> 
Devices
-----------------------
hp  CDDVDW TS-U633F HH05 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R,   DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential,   DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW   Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual   Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16,   RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2267249 (4643325952 bytes)
System
----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version: 4.7.0
Kernel: 2.6.35-22-generic
Used versions
----------------------
mkisofs: 1.1.10
cdrecord: 1.1.10
cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type : Removable CD-ROM
Version : 5
Response Format: 2
Capabilities :
Vendor_info : 'hp '
Identification : 'CDDVDW TS-U633F '
Revision : 'HH05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0015 (DVD-R/DL sequential recording)
Profile: 0x0016 (DVD-R/DL layer jump recording)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite) (current)
Profile: 0x0012 (DVD-RAM)
Profile: 0x0011 (DVD-R sequential recording)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0002 (Removable disk)
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Drive buf size : 1406976 = 1374 KB
FIFO size : 12582912 = 12288 KB
**/usr/bin/wodim: WARNING: Could not manage to find medium size, and more than 90 mins of data.**
Speed set to 2770 KB/s
Track 01: data 4428 MB
Total size: 5085 MB (503:49.9:cool: = 2267249 sectors
Lout start: 5085 MB (503:51/74) = 2267249 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.

Starting to write CD/DVD at speed 2.0 in real SAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
1 seconds.
0 seconds. Operation starts.

Waiting for reader process to fill input buffer ...** Errno: 5 (Input/output error)**, reserve track scsi sendcmd: no error
CDB: 53 00 00 00 00 00 22 98 71 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 05 00 00
**Sense Key: 0x5 Illegal Request, Segment 0**
**Sense Code: 0x72 Qual 0x05 (no more track reservations allowed) Fru 0x0**
Sense flags: Blk 0 (not valid)
cmd finished after 0.001s timeout 200s
**/usr/bin/wodim: Cannot open new session.**
input buffer ready.
Writing time: 0.038s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -multi -data -tsize=2267249s -
mkisofs
-----------------------

2267249
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using __*(...ixnaytheblahmay. This part is just filenames and stuff I omitted to make things less... long.*)
0.09% done, estimate finish Wed Mar 30 09:09:17 2011
0.11% done, estimate finish Wed Mar 30 09:09:17 2011
0.13% done, estimate finish Wed Mar 30 09:09:17 2011
0.15% done, estimate finish Wed Mar 30 09:20:04 2011
0.18% done, estimate finish Wed Mar 30 09:18:42 2011
0.20% done, estimate finish Wed Mar 30 09:17:39 2011
0.22% done, estimate finish Wed Mar 30 09:16:50 2011
0.24% done, estimate finish Wed Mar 30 09:16:09 2011
0.27% done, estimate finish Wed Mar 30 09:15:34 2011* (Not. Even. A full 1%.)*
mkisofs calculate size command:

-----------------------

/usr/bin/genisoimage  -gui -graft-points -print-size -quiet -volid  BaniMedia v01 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN  TRUEG AND MICHAL MALEK  -publisher -preparer -sysid LINUX -volset-size 1  -volset-seqno 1 -sort  /tmp/kde-ubuntu/k3bB16394.tmp -rational-rock  -hide-list  /tmp/kde-ubuntu/k3bm16394.tmp -joliet -joliet-long  -hide-joliet-list  /tmp/kde-ubuntu/k3bZ16394.tmp -no-cache-inodes  -full-iso9660-filenames  -disable-deep-relocation -iso-level 3  -path-list  /tmp/kde-ubuntu/k3bj16394.tmp

mkisofs command:

-----------------------

/usr/bin/genisoimage  -gui -graft-points -volid BaniMedia v01 -volset  -appid K3B THE CD  KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL  MALEK -publisher  -preparer -sysid LINUX -volset-size 1 -volset-seqno 1  -sort  /tmp/kde-ubuntu/k3bm16394.tmp -rational-rock -hide-list   /tmp/kde-ubuntu/k3bB16394.tmp -joliet -joliet-long -hide-joliet-list   /tmp/kde-ubuntu/k3bQ16394.tmp -no-cache-inodes -full-iso9660-filenames   -disable-deep-relocation -iso-level 3 -path-list   /tmp/kde-ubuntu/k3bL16394.tmp
_**Things I've tried/considered:**_
x  IS WODIM THE PROBLEM HERE? Because that's what always comes up when I   look up help. I need help installing cdrtools, though. It's telling me   stuff about how 'configure'-ing is outdated and something about   makefiles. My eyes are already bleeding and I haven't even begun to make   sense of things.
x So yes, my driver is compatible.[B]
x I'm using Ubuntu 10.10 on a USB drive.
x ...Permission problems? (Live-session user.)
[/B]x Checking if the files are the source of the problem (corruption).
**x I have no idea if my firmware is updated and have no idea in how to go about in doing so.**
x  I have no clue if other CD/DVD types and brands will work. I can't   really afford to find out. Seriously. I'm so broke... I could like...   Open a brokerage firm for lame puns.
x Writing in slower speeds...
x Pretty much everything a nub can even think to try.
[B]
Why I'm using ubuntu in the first place:[/B]

I  was defragmenting my hard drive. Power ran out on me. Really,  /really/  stupid move to do that without battery. STUFF GOT CORRUPTED.
And now something has to do something with disk partitions and I'm all like "wuhhh".
So yeah. My PC won't even get past Startup Repair now. Just stays there for hoouuuurrs.
So a friend of mine gave me ubuntu 10.10. Sotharyouhaveit.

_**SO YEAH. I like, really need to back up my stuff. That's practically my life right there.**_   I'm serious. Portfolio, music, writing... All of it. It's not all   backed up. I only have 8GB out of 150GB (which isn't that much anyway)   backed up. Just my graphics, inspiration collections, art resources, and   some of my old artwork, etc.

[I]Please, help meeeee.

[/I]**OH. And about Wine. **It's just like... Totally not working. The window pops up... And then dissappears. 
O _o I've got NO$GBA to work, so I can play Professor Layton. (My Nintendo DS' touch screen is totally broken.) But NO$Zoomer doesn't work with it. Visual Boy Advance doesn't work. A visual novel game I was playing isn't working. No other .exe works. Siiiigh. e _e

Oh. And like. Matroska codecs. HOW DO THEY WORK.

---

### Post by TeoBigusGeekus on 2011-03-31
Brasero and K3b go through cycles of working/not working the last few years.
I abandonded them and only use command line now.

Gather your data into a folder.
Create an iso of your data:
```
mkisofs -o imagename.iso -J /path/to/folder/
```
Then burn the iso to a dvd:
```
growisofs -dvd-compat -Z /dev/sr0=/path/to/iso/imagename.iso
```
Replace sr0 with whatever works in your system (dvd, cd, etc.)

I don't use wine and I stay away from matroska.

---

