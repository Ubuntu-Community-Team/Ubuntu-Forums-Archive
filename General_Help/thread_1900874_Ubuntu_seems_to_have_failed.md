---
title: "Ubuntu seems to have failed"
date: 2011-12-27
forum: General Help
---

### Post by TXbirder on 2011-12-27
Last week, while using Ubuntu, the image grayed out and I have no been able to get the OS to start up since.  In fact, I can't get past GRUB.

I have a dual-boot system with Win7 on one hard drive and 10.04 on the other.   I changed the boot sequence in BIOS and got the Live Disk to open once but not since.    Now all I get in GRUB is:
Loading Operating System...
Boot from CD/DVD:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

I noticed on the BIOS screen (see attached photo) that only one hard drive is listed.  I'm guessing that the Ubunti drive has failed.  But since I can't open anything, including Win7, I can't check the systems.

Do you agree  with my assessment  of the missing drive on the BIOS screen?  Shall I just buy a new drive and reinstall Ubuntu?

John

---

### Post by 2F4U on 2011-12-27
It may be worth checking the hdd connections and see if everything is properly connected. If everything is connected and the BIOS still doesn't show the second hdd, it must be completely damaged somehow and is probably not recoverable, except maybe by a professional data rescue service.

---

### Post by TXbirder on 2011-12-28
I checked and all were plugged in OK.  I disconnected one drive at a time to see if disconnecting the bad one would allow the system to start.  No luck with either drive.   
I don't know which drive has Win7 and which has Ubuntu on it.
Would it be practical to remove both and take them to a repair shop: identify which is which and identify the bad one, if one is bad?

Also, on the BIOS, I have Master and Slave.  Which is which- top or bottom in the photo?

I'll be sure to label them before reinstalling.

---

### Post by grahammechanical on 2011-12-28
You have sata drives. They do not have a master and slave relationship. See this link.

[http://www.seagate.com/ww/v/index.jsp?vgnextoid=2b089d2c3c90e010VgnVCM100000dd04090aRCRD&locale=en-US]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=2b089d2c3c90e010VgnVCM100000dd04090aRCRD&locale=en-US")

It looks like you have two Western Digital Caviar drives. Are they the same size? If not, then you might be able to work out which drive is which if you can remember which OS was on which size drive.

Something is strange about your machine because those messages are recording the SATA drives as IDE drives. The left side of the screen is cut off in the image but I am guessing each of those channels is marked as IDE. And yes only one of the drives is showing up.

Do you have the motherboard user guide? Does that give any information about which ports to plug the drives in?

As an outright guess I ask, have you done something in the BIOS to set the drives as IDE and not SATA. I ask because that photograph of the monitor screen is showing the POST messages not the BIOS. That image shows that you are not yet in the BIOS setup utility.

Regards.

---

