---
title: "hp scanjet 5550c scanner"
date: 2010-08-31
forum: General Help
---

### Post by AgentZ86 on 2010-08-31
Updated as of 9-1-10
I think my scanners are defective so I tossed them until I can get another known working 5550c
I can't be sure they were defective, however I had similar problems on a Windows machines also.
When nstalling my scanners on Linux is was freezing and I assumed some Linux problem, however I re-tested on Windows with the same problem.
Freezing in the middle of the initial scan.
Anyhow, I left this post up so if I come across another known working scanner I can retest this subject

Initial Post Below:

Hi

Background info when trying to install HP scanjet 5550c

Xsane finds the scanner and attempts to scan but then ends with I0 error

[LIST]
[*]Using Karmic Koala 9.10 64bit Fully updated
[*]Xsane working perfect with an older HP 6300
[*]I installed an hp 5550c and it's suppose to work (complete) according to sane site:
[*][http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)
[*]With backend version of hp5590 (1.0.5) according to the sane site
[*]I see my libsane and sane-utils in synaptic are versions 1.0.20
[*]When starting xsane the scanner is detected and I hit the xsane scan button as I've always done
[*]The scanner starts and attempts to scan but then just sort of does a half scan and freezes and then xsane says recieving data in the data bar, but then it freezes to and ends with IO error
[/LIST]

If there is something I might do to get this working.
I've read about various bugs with sane version 1.0.20 where some had working scanners with versions 1.0.19 then after updates their scanner quit working etc.
I don't think this relates to my topic because my scanner is recognized and partially works.

I also have a HP 8390 I would try but nothing on the sane site about it at all, so likely that will not work.

Also I've tried this:
>  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1205 [hp scanjet scanner], chip=HP5550/5590/7650) at libusb:001:014
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

and this:
scanimage -L
> WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `hp5590:libusb:001:014' is a HP 5550 Workgroup scanner


Please advise
Thanks

P.S
I'm assuming 1.0.5 is lower version then 1.0.20 ?

---

### Post by AgentZ86 on 2010-10-14
I have now tested a working scanner and confirmed that the old scanjet 6300 and 5590 are still works on other ubuntu 9.10 32bit OS machines

So currently on a Ubuntu 9.10 64bit machine fully updated can detect the scanner and attempt a scan. But fails with I/O error

HP 5590 and is completely supported with sane according to the site.
Please advise what changed with xsane or Ubuntu 9.10 updates that is not allowing my scanners to work anymore ?
This appears to be with all scanners I've tried since my 6300 quite working with the ubuntu updates a while back

I really would like to be able to scan somehow 

Please help me diagnose this topic
Thanks

---

### Post by AgentZ86 on 2010-10-20
I tested all my scanners on ubuntu 9.10 32bit OS
And back on 9.10 64bit OS and they just won't work properly on 64bit OS
I don't know where to start ?
They seem to be detected, and will actually scan maybe one page if lucky ? but then the error code
Then if I close xsane and open again it won't find the device
I turn off the scanner and on again, then open xsane and if finds it again.
But scans partially and you can see the scanner scan the page.
The meter shows (receiving data) and then the error pops up after waiting a while.
All my scanners use to work great on 64bit ? What happened ?

Did I install something that effected it ? did updates break something ? 
Where do I start ?

Please advise

---

