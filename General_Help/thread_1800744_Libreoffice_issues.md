---
title: "Libreoffice issues"
date: 2011-07-09
forum: General Help
---

### Post by smcrossman on 2011-07-09
Since I reformatted and reinstalled natty 64bit I have been unable to run any office applications.  Whenever i try to open libreoffice it shows the splash screen and teh progress bar at about 15-25% and then locks up the entire computer.  cntl+alt+del no longer works, cntl+ shift+alt+del does not work.  I have to actually use the power button to shut down to the computer wait and then reboot.  I have uninstalled and reinstalled libre office...still the same thing.  Today...really needing access to word processing, I went and attempted to install open office.  after the installation, I only have libre office.  It still locks up everything.  I went and uninstalled all the libreoffice packages, which also uninstalled open office.  I try to install open office and it won't because it "depends" on libre office.

Is there another option or alternative that is similar and functions as well as openoffice/libreoffice?  I was using open office in windows so I'm comfortable with and trust its functionality.  I'm really, really going to need to have spreadsheet and word processing funtionality soon....I have a lot of records to create, update and use.

Also everything is coming up as unauthenticated. It will allow me to go ahead and install most of it, but what settings do I have wrong that even basic ubuntu installed packages (evolution, etc) show up as not authenticated in synaptic package manager.?

---

### Post by techunit on 2011-07-09
More information would be benificial, do you know if your running enough ram or have enough swap space? Or can you be sure you don't have a botched Libre install?

lets assume a botched libre install.

```
sudo apt-get purge libreoffice-common
```
```
sudo apt-get update
```
```
sudo apt-get install libreoffice libreoffice-gnome
```

hope this helps

---

### Post by smcrossman on 2011-07-09
Thank you. That didn't help, but it was a good thing to check it by using the apt-get instead of just doing synaptic package manager uninstall/reinstall/and uninstall.  I've also tried  using auto-apt run to see if I could figure out why it was hanging but it just locked up like always and didn't accomplish anything.

From hardinfo:

-Computer-
Processor        : 3x AMD Phenom(tm) 8400 Triple-Core Processor
Memory        : 3927MB (820MB used)
Operating System        : Ubuntu 11.04
User Name        : suzanna (Suzanna Crossman)
Date/Time        : Sat 09 Jul 2011 07:31:25 PM EDT
-Display-
Resolution        : 1440x900 pixels
OpenGL Renderer        : GeForce 6150SE nForce 430/PCI/SSE2
X11 Vendor        : The X.Org Foundation
 
ATA WDC WD3200AAJS-2
-Version-
Kernel        : Linux 2.6.38-8-generic (x86_64)
Compiled        : #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
Distribution        : Ubuntu 11.04
-Memory-
Total Memory        : 3927336 kB
Free Memory        : 2499504 kB
Buffers        : 76816 kB
Cached        : 599532 kB
Cached Swap        : 0 kB
Active        : 695520 kB
Inactive        : 476844 kB
Active(anon)        : 496816 kB
Inactive(anon)        : 2920 kB
Active(file)        : 198704 kB
Inactive(file)        : 473924 kB
Unevictable        : 16 kB
Mlocked        : 16 kB
Virtual Memory        : 4061180 kB
Free Virtual Memory        : 4061180 kB
Dirty        : 0 kB
Writeback        : 0 kB
AnonPages        : 496028 kB
Mapped        : 137740 kB
Shmem        : 3724 kB
Slab        : 59700 kB
SReclaimable        : 34280 kB
SUnreclaim        : 25420 kB
KernelStack        : 2960 kB
PageTables        : 32164 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 6024848 kB
Committed_AS        : 2041264 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 150232 kB
VmallocChunk        : 34359563980 kB
HardwareCorrupted        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 164736 kB
DirectMap2M        : 2848768 kB
DirectMap1G        : 1048576 kB

The Swap portion of the HD is 4.2 GB
I'm not sure this pc has ever actually used swap space though...seems whenever I've looked at anything that listed swap used it has been 0.  But I don't know much about that kind of stuff.

---

### Post by Hagar Delest on 2011-07-12
You can try to install the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

It applies for both OOo and LibO, you can even run both in parallel.

Try also to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by AlphaLexman on 2011-07-12
Try starting in a terminal from the command line...
```
oowriter -norestore
```From the man page:
> Disables restart and file recovery after a system crash. It is possible
OOo  will  try  to restore a file it keeps crashing on, if that happens
-norestore is the only way to start OOo.


---

### Post by smcrossman on 2011-07-17
Neither option worked for me.  But with a little more time I started coming across more programs that wouldn't open and started having more and more frequent complete lockups.

Since it was a fairly fresh install and I hadn't managed to restore my backed up files yet I just did a totally clean installation.  Things seem to be operating fairly normally again.  I suspect that I had installed some packages to "try out" or explore and/or deleted some packages that I had installed and decided I didn't like that had corrupted something along the way.  Now I just need to be a lot more cautious about what I choose to "try out" and make sure that uninstalling them doesn't uninstall files needed elsewhere.  I am learning my lessons the hardway, but I am learning them!

Thanks for the help!

---

