---
title: "Quicken 2000 basic won't run in Ubuntu 10.04 WINE"
date: 2010-11-10
forum: General Help
---

### Post by daldude on 2010-11-10
I had to upgrade to Ubuntu 10.04 after 9.04 stopped being supported and now I can't run Quicken 2000 Basic in WINE anymore when it ran just fine under 9.04 using WINE 
When I try to install it from the CD ROM it gives me this error

**The file '/media/QWINMMR1F/install.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.**

So I copied all the files from the Quicken CD  to my hard drive and installed it from that folder and it completed installation  without any installation errors but when I run Quicken and try to open the qdata.qdf file Quicken gives me a "can't open file" error.

I then removed WINE and installed the latest BETA Version now I can install from the CD but still get the "can't open file" error from Quicken.

It worked fine under 9.04 and WINE and I could update the info in Ubuntu and it would show up under Windows and if I'd update in Windows it would show up under Linux.
Now in Ubuntu 10.04 it does not work.

How can I fix this problem?

---

### Post by daldude on 2010-11-15
I got it to work, I had to copy the qdata.qdf file to a different partition other then the Windows XP Boot Partition and now it loads ok, why it had a problem with the XP Boot partition is beyond me because it did not have that problem in 9.04.
But it works so I'm satisfied.

---

