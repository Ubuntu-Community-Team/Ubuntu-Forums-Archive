---
title: "CD/DVD Burning Problems"
date: 2006-05-21
forum: General Help
---

### Post by Dantrag on 2006-05-21
Hello everyone it's me again. Got a new issue ](*,) 
I am unable to burn a cd or dvd. It goes through the motions and the light on my drive even lights up and flashes like it's really doing something big but when you put the disc back in it's blank. I have tried using the Serpentine program, K3B, Gnomebaker, and QDVD. I have a LITE-ON DVDRW SOHW-1693S and am running kernel 2.6.12-9-386. I have combed these forums looking for something that resembles my issue but came up empty. I will post the debug output from K3B in hopes that it's a real simple fix. Let me know if anyone needs any more information.

I had to take out all the tracking information to get it small enough to fit in this post.
K3B Debug Output:
System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.5.1
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
LITE-ON DVDRW SOHW-1693S KS0A (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

K3b
-----------------------
Size of filesystem calculated: 315710

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'DVDRW SOHW-1693S'
Revision       : 'KS0A'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1895168 = 1850 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   616 MB        
Total size:      708 MB (70:09.49) = 315712 sectors
Lout start:      708 MB (70:11/37) = 315712 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -12900 (97:10/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 4 5
  recommended erase/write power: 3
  A1 values: 02 4A B0
  A2 values: 5C C6 26
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Manufacturer is unknown because of the orange forum embargo.
As the orange forum likes to get money for recent information,
it may be that this media does not use illegal manufacturer coding.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 44137
Forcespeed is OFF.
Starting to write CD/DVD at speed 4 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01: Total bytes read/written: 646574080/646574080 (315710 sectors).
Writing  time: 1068.375s
Average write speed   4.0x.
Min drive buffer fill was 45%
Fixating...
Fixating time:   84.117s
/usr/bin/X11/cdrecord: fifo had 10185 puts and 10185 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 10096 times full, min fill was 92%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -tao driveropts=burnfree -eject -multi -xa -tsize=315710s - 

mkisofs
-----------------------

Total translation table size: 0
Total rockridge attributes bytes: 1194
Total directory bytes: 4096
Path table size(bytes): 70
Max brk space used 21000
315710 extents written (616 MB)

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-adambrady/k3bNal0ga.tmp -rational-rock -hide-list /tmp/kde-adambrady/k3bQW2jpc.tmp -joliet -hide-joliet-list /tmp/kde-adambrady/k3bhOzfPb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-adambrady/k3bk5tZlc.tmp

---

### Post by zentus on 2006-05-22
I have the exact same problem.  Any suggestions anyone?

---

### Post by Dantrag on 2006-05-22
I'm sure that it's something simple that we are just overlooking. Perhaps one of the Ubuntu Sage's can shed some light on the situation. *beg*

---

### Post by Dantrag on 2006-05-23
Bump in a shameless pleading for help.

---

### Post by Dantrag on 2006-05-23
I tried again with Graveman and cdrecord in Terminal. Still the same issue. I think that it probably has something to do with these errors that I am getting in the output:
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted


In /usr/bin there is a folder with an arrow in the lower left corner called X11. Inside X11 is an exact duplicate of /usr/bin including another X11 folder with an arrow. I'm assuming that it's some kind of shortcut. Anyone have any Ideas? I have asked here and in IRC for help and the best I can be told is to wait for Dapper in June!!! I really don't want to wait till June to be able to have a fully functioning desktop environment.

---

### Post by kcr on 2006-05-24
I spent ages trawling the forum trying to get my burner going. Until I tried a different set of CD's. I had a bad batch and slowly worked through the 20 something stack. Try a different CD Blank. Sounds crazy but worth a try.

---

### Post by Dantrag on 2006-05-24
Good tip kcr. I have tried several different brands and types of media. All of these will burn in windows so I don't believe this is the issue.

---

### Post by diw on 2006-05-24
I'm not new to linux but am new to Ubuntu and I can't burn a thing.  I have an LG dual layer dvd drive and have tried to use the inbuilt cd/dvd recorder, k3b and gnome baker but to no avail.  The eroor message on gnome baker is

Executing 'mkisofs -V GnomeBaker data cd -p David Wrigley -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -gui -graft-points Annie Lennox=/home/david/My_Documents/Music_Lossless/Annie Lennox | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
:-[ SET STREAMING failed with SK=5h/ASC=26h/ACQ=00h]: Input/output error

Can anyone shed any light on this?

---

