---
title: "Suddenly my pc can not burn CDs or DVDs."
date: 2011-03-27
forum: General Help
---

### Post by BSG Fan on 2011-03-27
Here is my problem using K3B when writing Multi-session Project
:


&#8221;
  [COLOR="Lime"]Writing CD-R

  Using Wodim 1.1.10.

  Starting TAO to writing at 48x speed

  performing Optimum Power calibratpo;;p;9;n

  starting disk write

  mkisofs crashed

  cdrecord has no permission to open the device

  You may use K3bsetup to solve this problem[/COLOR]

"

Folks, I have the same problem with the other cd-burner programs, such as:
Brasero Disk Burner, Gnome Baker CD/DVD Writer, xfBurn, and CD/DVD Creator.

Why all the programs are malfunctioning since yesterday?

I un-installed some of them, re-started the pc, but the problem continues...

Any idea?

==


Here is the &#8220;Debugging Ouput&#8221; for the K3B:
Devices

-----------------------

TSSTcorp CDDVDW SH-S223C SB03 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]



K3b::IsoImager

-----------------------

mkisofs print size result: 110167 (225622016 bytes)



System

-----------------------

K3b Verspo;;p;9;n: 1.91.0

KDE Verspo;;p;9;n: 4.4.5 (KDE 4.4.5)

QT Verspo;;p;9;n:  4.6.2

Kernel:      2.6.32-30-generic



Used verspo;;p;9;ns

-----------------------

mkisofs: 1.1.10

cdrecord: 1.1.10



cdrecord

-----------------------

/usr/bin/wodim: Operatpo;;p;9;n not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.

scsidev: '/dev/sr0'

devname: '/dev/sr0'

scsibus: -2 target: -2 lun: -2

Linux sg driver verspo;;p;9;n: 3.5.27

Wodim verspo;;p;9;n: 1.1.10

SCSI buffer size: 64512

Beginning DMA speed test. Set CDR_NODMATEST environment variable if device

communicatpo;;p;9;n breaks or freezes immediately after that.

TOC Type: 3 = CD-ROM XA mode 2

Driveropts: 'burnfree'

Device type    : Removable CD-ROM

Verspo;;p;9;n        : 5

Response Format: 2

Capabilities   : 

Vendor_info    : 'TSSTcorp'

Identificatpo;;p;9;n : 'CDDVDW SH-S223C '

Revispo;;p;9;n       : 'SB03'

Device seems to be: Generic mmc2 DVD-R/DVD-RW.

Current: 0x0009 (CD-R)

Profile: 0x002B (DVD+R/DL) 

Profile: 0x001B (DVD+R) 

Profile: 0x001A (DVD+RW) 

Profile: 0x0016 (DVD-R/DL layer jump recording) 

Profile: 0x0015 (DVD-R/DL sequential recording) 

Profile: 0x0014 (DVD-RW sequential recording) 

Profile: 0x0013 (DVD-RW restricted overwrite) 

Profile: 0x0012 (DVD-RAM) 

Profile: 0x0011 (DVD-R sequential recording) 

Profile: 0x0010 (DVD-ROM) 

Profile: 0x000A (CD-RW) 

Profile: 0x0009 (CD-R) (current)

Profile: 0x0008 (CD-ROM) 

Profile: 0x0002 (Removable disk) 

Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).

Driver flags   : MMC-3 SWABAUDpo;;p;9; BURNFREE 

Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

Drive buf size : 720896 = 704 KB

FIFO size      : 12582912 = 12288 KB

Speed set to 8467 KB/s

Track 01: data   215 MB        

Total size:      247 MB (24:28.92) = 110169 sectors

Lout start:      247 MB (24:30/69) = 110169 sectors

Current Secsize: 2048

ATIP info from disk:

  Indicated writing power: 4

  Is not unrestricted

  Is not erasable

  Disk sub type: Medium Type A, low Beta category (A-) (2)

  ATIP start of lead in:  -12508 (97:15/17)

  ATIP start of lead out: 359845 (79:59/70)

Disk type:    Short strategy type (Phthalocyanine or similar)

Manuf. index: 22

Manufacturer: Ritek Co.

Blocks total: 359845 Blocks current: 359845 Blocks remaining: 249676

Starting to write CD/DVD at speed  48.0 in real TAO mode for multi sesspo;;p;9;n.

Last chance to quit, starting real write in    2 seconds.

   1 seconds.

   0 seconds. Operatpo;;p;9;n starts.

Waiting for reader process to fill input buffer ... input buffer ready.

Performing OPC...

Starting new track at sector: 0

Track 01:    0 of  215 MB written.

Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error

CDB:  2A 00 00 00 00 7C 00 00 1F 00

status: 0x2 (CHECK CONDITpo;;p;9;N)

Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 02 00 00

Sense Key: 0x3 Medium Error, Segment 0

Sense Code: 0x73 Qual 0x02 (power calibratpo;;p;9;n area is full) Fru 0x0

Sense flags: Blk 0 (not valid) 

cmd finished after 19.379s timeout 40s

/usr/bin/wodim: A write error occured.

/usr/bin/wodim: Please properly read the error message above.

write track data: error after 253952 bytes

Writing  time:   25.050s

Average write speed  58.7x.

Fixating...

Fixating time:    0.004s

/usr/bin/wodim: fifo had 196 puts and 5 gets.

/usr/bin/wodim: fifo was 0 times empty and 2 times full, min fill was 98%.

BURN-Free was never needed.



cdrecord command:

-----------------------

/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=48 -tao driveropts=burnfree -multi -overburn -xa -tsize=110167s -



mkisofs

-----------------------

110167

I: -input-charset not specified, using utf-8 (detected in locale settings)

Using
 etc ...
 etc...
 etc....

Using SOME DATA00E.OD;1 for  0- MY DATA/some data (190) P. 18.odt (some data (189) P. 18.odt)

  0.45% done, estimate finish Sun Mar 27 13:41:11 2011

  0.91% done, estimate finish Sun Mar 27 13:43:00 2011

  1.36% done, estimate finish Sun Mar 27 13:42:24 2011

  1.83% done, estimate finish Sun Mar 27 13:42:05 2011

  2.28% done, estimate finish Sun Mar 27 13:41:54 2011

  2.73% done, estimate finish Sun Mar 27 13:41:47 2011

  3.18% done, estimate finish Sun Mar 27 13:41:42 2011

  3.63% done, estimate finish Sun Mar 27 13:41:38 2011

  4.08% done, estimate finish Sun Mar 27 13:41:35 2011

  4.55% done, estimate finish Sun Mar 27 13:41:32 2011

  5.00% done, estimate finish Sun Mar 27 13:41:31 2011

  5.46% done, estimate finish Sun Mar 27 13:41:29 2011



mkisofs calculate size command:

-----------------------

/usr/bin/genisoimage -gui -graft-points -print-size -quiet -tttttttid 1- Bookmarks -tttttttset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -tttttttset-size 1 -tttttttset-seqno 1 -sort /tmp/kde-user/k3bad4758.tmp -ratpo;;p;9;nal-rock -hide-list /tmp/kde-user/k3bwR4758.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-user/k3bWa4758.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-user/k3bmI4758.tmp



mkisofs command:

-----------------------

/usr/bin/genisoimage -gui -graft-points -tttttttid 1- Bookmarks -tttttttset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -tttttttset-size 1 -tttttttset-seqno 1 -sort /tmp/kde-user/k3bcn4758.tmp -ratpo;;p;9;nal-rock -hide-list /tmp/kde-user/k3bap4758.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-user/k3bXj4758.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-user/k3bVf4758.tmp

---

### Post by linuxuser12345 on 2011-03-27
Have you tried a simple computer restart? How about reinstalling Ubuntu?

---

### Post by cottfcfan on 2011-03-27
Reinstalling Ubuntu might be a bit drastic.
Check if Nero Linux works it can be downloaded from here;
[http://www.nero.com/eng/linux4.html](http://www.nero.com/eng/linux4.html)

---

### Post by BSG Fan on 2011-03-28
Confused...

I re-formatted the pc
and the problem continues.
No CD/DVD burning program burns.

Any idea?

:(

---

### Post by techman2go on 2011-03-28
I have a similar problem.   I can burn CD/DVDs if I boot to Windows XP but not in ubuntu 10.10.   I tried burning a CD and it got to the end and started to finish up but the time to finish kept getting longer and longer.  I forced it to quite and ejected the disk.   Inserted the CD and the files could not be read.   Could this be related to not being able to play a movie on the DVD as well.   Seems the player needs a plug-in but can't find it.   Seems like something is missing in the control of my CD/DVD-R/RW unit.   This is a USB unit as the internal is a CD-ROM only.  How do I determine the cause of these problems and find a fix?

---

### Post by BSG Fan on 2011-03-28
Hey folks:

My cd/dvd burner is "Super Writemaster driver, SpeedPlus"

I searched the net and it says that is a Samsung

How (where in my pc) can I know what is the properties/description of such cd burner?

Do I have to download some update for it?  Which one, so?

Why it worked for months and suddenly after yesterday it does not work more?  It's ruined?


==
I do not know if it is related but I went to 
System
Administration
Hardware Drivers
and I found that "No proprietary drivers are in use on this system" with 3 different drivers no activated...  What it means?  That has something to see with my burner problem?

Help

:(

---

### Post by BSG Fan on 2011-03-28
techman2go:
I hope we find the solution.  I can not burn my data as before and that is a super headache for me.  Let's see

:confused:

---

### Post by gzuz420 on 2011-03-29
I am having the same problem tonight. I tried to burn a data cd and got the same error, before and after restarting my PC. I am running Linux Mint 9 (gnome), and burned dozens of DVDs and CDs for years without this problem. Also, FWIW my Linux box has not been connected to the internet for several weeks and I had no problems burning discs 3 days ago which was the last time that I attempted to before tonight.  Again, I burned discs with no problems at all 3 days ago, the computer has not been connected to a modem, and now I am having the "mkisofs crashed. cdrecord has no permission to open the device. you may use k3bsetup to solve this problem."  Hopefully this will help you narrow down the issue, as afaik it has GOT to be related to one of the software components having a conflict related to the date. Will try setting the clock back a few days on my Linux box and see if this makes a difference, and will post back IF it DOES make a difference!

---

### Post by gzuz420 on 2011-03-29
Ok, so after rebooting no problem prior to my last post, I went ahead and set the date back 3 days on my Linux Mint 9 Gnome PC clock. I then found that K3B was unable to detect the blank CD in the drive, but Mint/Gnome was able to detect that it was there upon eject/reinsert. So I closed K3B and re-opened the burning app and still had the issue of it being unable to see the blank disc in the drive.    Next, with the clock still set back 3 days, I restarted the PC.   Got to the Linux Mint splash screen and got this message:   "Errors were found while checking the disk drive for /"  and now it will not finish booting into the OS. What on earth is going on here? The only change that I made was to swing the clock back 72 hours.

---

### Post by BSG Fan on 2011-03-29
Any idea?

---

### Post by held7over on 2011-04-07
Has anybody figured out why this is happening and how to fix it?

I get "mkisofts crashed" at the beginning of a burn OR it goes through the whole burn and then errors at 99% or 100% just before it closes, saying, "Input/Output error"...this last creates a dvd that is not then recognized by the computer when re-inserted. In fact, no computer recognizes it.

---

