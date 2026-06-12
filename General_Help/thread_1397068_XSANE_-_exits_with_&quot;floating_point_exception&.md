---
title: "XSANE - exits with &quot;floating point exception&quot; in 8.04.4 using Scanpartner 15c/SCSI"
date: 2010-02-02
forum: General Help
---

### Post by ralph_804scanner on 2010-02-02
I'm using a SCSI scanner with Ubuntu 8.0.4.4 on a Pentium III, and an adaptec 2906 PCI SCSI card.

xsane 0.995 is the version of SANE I am using.

I've avoided  installing Ubuntu 9.10 / karmic because of numerous problem reports.

XSANE starts up, and allows me to set up my settings for scanning using the ADF.  However, I immediately get a "floating point exception" about the time sane starts sending commands to the scanner.

All I can see in /var/log/syslog are these lines, which were also reported by a fellow in a German ubuntu forum (he was using a Scanpartner 600c) - his message is at this URL:

[http://forum.ubuntuusers.de/topic/xsane-floating-point-exception/#post-2293921](http://forum.ubuntuusers.de/topic/xsane-floating-point-exception/#post-2293921)

Feb  2 09:29:49 ubuntu kernel: [  407.260000] ppdev0: registered pardevice
[B]Feb  2 09:29:49 ubuntu xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1
[/B] 
Feb  2 09:29:49 ubuntu kernel: [  407.309174] ppdev0: unregistered pardevice
Feb  2 09:31:22 ubuntu kernel: [  500.077824] kjournald starting.  Commit interv
al 5 seconds

Two questions:
1) How can I turn on additional debugging from SANE?

2) What release of SANE were tested with the Scanpartner 15C?  I need to scan several hundred pages of documents for a futures studies class I'm evaluating.  This all worked much better with a RedHat release, but I don't have easy access to that any more.

Thank you,

- Ralph

---

