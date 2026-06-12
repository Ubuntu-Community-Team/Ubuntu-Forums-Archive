---
title: "gwizard version string problem(?)"
date: 2012-09-23
forum: General Help
---

### Post by arvevans on 2012-09-23
What is this?

[INDENT]dpkg: warning: parsing file '/var/lib/dpkg/available' near line 34936 package 'gwizard.56bbed34ae4ebf4b3593056f8e0b8ea604a1db20.1':
 error in Version string 'v1': version number does not start with digit[/INDENT]

and this?

[INDENT]Reading package lists... Done
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
[/INDENT]

*[FONT="Arial Narrow"]UBUNTU 12.04, Gnome Classic, AMD Dual-core 3800, 4GB RAM [/FONT]*

---

### Post by arvevans on 2012-09-27
Apparently nobody else knows what these error messages might be.

---

### Post by arvevans on 2012-10-29
Guess I can mark this one as SOLVED.  No one helped and I couldn't figure it out.  It apparently went away when I upgraded from 12.04 to 12.10.  Now I have a whole new set of problems to wade through.    :confused:

---

### Post by arvevans on 2012-11-09
Changed this one from SOLVED back to UNSOLVED.  The problem has come back again after a couple of days using the new Ubuntu 12.10 release.

[INDENT]Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 37452 package 'gwizard.56bbed34ae4ebf4b3593056f8e0b8ea604a1db20.1':
 error in Version string 'v1': version number does not start with digit
[/INDENT]

A bit of research seems to indicate that "gwizard" may be part of a G-code editor for CNC machining tools.  Since I do have a CNC milling machine and do use CAD programs on this computer to generate G-Code for driving EMC2 and the mill, this may be where this came from.  Now the question is HOW DO I GET RID OF THE VERSION NUMBER ERROR?

---

### Post by arvevans on 2012-11-15
Okay...I can now change this back to "SOLVED".

After much research, some trepidation, and a great fear of killing my system...I did "**sudo vi /var/lib/dpkg/available**" and edited the offending stanza out of dpkg.  I have no idea if this was the proper way to do this, but it does seem to have worked.  **sudo apt0-get update** and **sudo apt-get upgrade** still seem to work properly and nothing appears to be broken.

:)

---

