---
title: "&quot;Routine check of drive&quot; freezes startup"
date: 2010-10-03
forum: General Help
---

### Post by techiewannabe on 2010-10-03
When I power up my computer, Ubuntu wants to do a "Routine Check of Drives." However, the system never boots up thereafter. It stops after about 7 - 15% of the system has been checked. (As far as as I can tell, it never stops at the same percentage.) The only way I can get my system to work is by rebooting it again wile hitting the 'escape' key. 

Your help would be appreciated.

Techiewannabe

---

### Post by dcstar on 2010-10-04
> **techiewannabe said:**
> When I power up my computer, Ubuntu wants to do a "Routine Check of Drives." However, the system never boots up thereafter. It stops after about 7 - 15% of the system has been checked. (As far as as I can tell, it never stops at the same percentage.) The only way I can get my system to work is by rebooting it again wile hitting the 'escape' key. 


Do you wait long enough for it to complete?, and that can mean far more than a couple of minutes.

---

### Post by Mark Phelps on 2010-10-04
When the filesystem check encounters bad blocks or files, it slows down because it tried over and over again to read the block or file.  That looks like it's stopped, but it's really trying to get past the bad block or file.

If it keeps stopping at different places, that either means you have a bunch of bad blocks or it means that you drive is failing and new bad blocks are appearing all the time.

Either way, you need to let it finish its filesystem checking.

---

### Post by MooPi on 2010-10-04
What Mark said should be followed. If you have external drives attached that may be slowing the boot process as well. Disconnect any external drives or usb devices that are detected as hard drives and see if that makes a difference.

---

