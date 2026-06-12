---
title: "Undo Persistence in LiveUSB (Live CD on USB)"
date: 2010-01-17
forum: General Help
---

### Post by CrazedKeebler on 2010-01-17
[SIZE=2]Hello all,

I have created a bootable flash drive with 9.10 (Karmic) and enabled persistance mode in order to create settings and alter the installed programs. The trick is: I've gotten to the point that I have worked out the web problems (ie. flash, java, codecs, etc.) and assembled a good collection of software so that a person using the LiveUSB as a demo of Ubuntu can actually have a fully functional experience instead of the bare-bones LiveCD; however, I do not want further changes taking place. 

I am trying to find a means of undoing persistence so that any further changes are discarded at startup, but everything that has been installed & changed up to this point will remain. Preferably, I would like a way to go back and update/install more, but I understand this may be a one-time deal.

Any ideas?

Thanks!
-Keebler
[/SIZE]

---

### Post by C.S.Cameron on 2010-01-17
I believe that once your casper-rw file, (or partition) is full you can no longer write to it. But I guess someone could delete files then write more.
The following page tells how to make a custom Live CD, and thus a custom Live USB.
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Perhaps the casper-rw file can be made read only??? You can find this file under filesystem/cdrom when booted from the flash drive.

Edit
I tried making casper-rw read only but it is still persistent.

---

