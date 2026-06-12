---
title: "Strange cdrecord error message burning from CUE file"
date: 2006-05-06
forum: General Help
---

### Post by glug101 on 2006-05-06
Ok, it's a measure of my own laziness that I have not searched longer for this.  However, I am really annoyed with this issue because it seems so straight forward. :confused: 

Anywho, here is the issue.  I am trying to burn a cd from a CUE file.  

Sample of CUE file
```
FILE "track-01.wav" WAVE

  TRACK 1 AUDIO

   INDEX 01 00:00:00

FILE "track-02.iso" BINARY

  TRACK 2 MODE1/2048

   PREGAP 00:03:00

   INDEX 01 00:00:00

FILE "track-03.wav" WAVE

  TRACK 3 AUDIO

   PREGAP 00:02:00 

   INDEX 01 00:00:00
```

So far (according to documentation) so good.  Now, when I try to burn the actual disc, I use the following command:

```
cdrecord -sao cuefile=Ys\ Book\ 1\&2.cue
```

And here is the output:

```
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-21-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'TSSTcorp'
Identifikation : 'CD/DVDW TS-H552U'
Revision       : 'US03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
cdrecord: Only one FILE allowed on line 4 in 'Ys Book 1&2.cue'
```

Errr... Only one FILE allowed?  I thought I only had one file listed.  If anybody has an idea as to what might be causing this, I would be very thankful.

Thanx a bunch in advance!! 
:D

---

### Post by TitusDalwards on 2006-05-06
have you checked the file pemissions?

---

### Post by glug101 on 2006-05-06
hmmm, I hadn't thought of that.  However, in this case it doesn't matter.  All files were created and attempted to burn using the same user account:(  Trying to run the cdrecord command using sudo gives the same error message.

Not sure, but can cdrecord only handle one file when using a cue file?  Do I just have to get creative with the command line?

---

### Post by TitusDalwards on 2006-05-06
cue files are normally not recognized,
you need to convert them to a iso first, witch can be done with bchunk.

```
bchunk binfile.bin cuefile.cue myisofile.iso
```

---

