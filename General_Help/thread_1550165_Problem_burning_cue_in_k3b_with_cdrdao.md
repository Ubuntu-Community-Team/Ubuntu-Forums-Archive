---
title: "Problem burning cue in k3b with cdrdao"
date: 2010-08-10
forum: General Help
---

### Post by ShadowWraith on 2010-08-10
I cannot get KDE to burn a cue/BIN image using DAO (the only available option)

Given error message:
```
cdrdao returned an unknown error (code 1).
```
The used device is a hp cd writer, but I get the same error on the other drive as well.
Debugging output:
```
Devices
-----------------------
_NEC DVD_RW ND-3550A 1.04 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite] [%7]
HP CD-Writer+ 8000 2.5C (/dev/sr1, CD-R, CD-RW, CD-ROM) [Error] [TAO, RAW, RAW/R16, RAW/R96R] [%7]

System
-----------------------
K3b Version: 2.0.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-24-generic

Used versions
-----------------------
cdrdao: 1.2.2

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/sr1 --driver generic-mmc:0x00000010 --speed 4 -n -v 2 --force --remote 23 /tmp/kde-david/k3bBF4103.tmp.cue
```

Can anyone make sense of this?

---

### Post by ShadowWraith on 2010-08-10
Okay, I checked what the problem was by running the command in the debug info directly, and got this error message:
```
Using libscg version 'ubuntu-0.8ubuntu1'                                                                                                           

/dev/sr1: HP CD-Writer+ 8000    Rev: 2.5C
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0010)

WARNING: Cannot get flags of remote stream: Bad file descriptor
Starting write simulation at speed 2...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot setup write parameters for session-at-once mode.
ERROR: Please try to use the 'generic-mmc-raw' driver.
ERROR: Simulation failed.

```
So I ran it with the generic-mmc-raw driver (option --driver generic-mmc-raw:0x00000010) -- I just added in the "-raw" and kept the hex number; I don't know what it represents.

The burn seems to be working so far. Is there a way to set KDE to use the generic-mmc-raw driver for all .cue files?

---

### Post by ShadowWraith on 2010-08-10
I solved the problem and finally burned the .cue by going to
Settings->Configure K3b and selecting Programs from the sidebar, going to the User Parameters tab.
I added in --driver generic-mmc-raw:0x00000010 under cdrdao, which made cdrdao run with the compatible driver and the disc burned.

Victory!

---

