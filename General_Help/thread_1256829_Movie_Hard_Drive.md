---
title: "Movie Hard Drive"
date: 2009-09-03
forum: General Help
---

### Post by patdundee on 2009-09-03
Hi Guys
 
Ubuntu 8 Server
 
I have a crashed system where the board has gone down. Is it possible to just move the Hard drive from the crashed system to a new system without losing any of the date etc. Currently I have websites joomla mysql etc etc installed on the drive on the crashed system. Can this just be pulled out and moved to a new system without lose of anything
 
Many thanks

---

### Post by P4man on 2009-09-03
does the drive also contain ubuntu itself?
Either way, if the drive isnt damaged, it should work. You will probably even be able to boot from it, if it was bootable.

---

### Post by patdundee on 2009-09-03
Hi P4Man
 
Yes it has ubuntu fully installed. Much appreciate the reply. I will give it a try later (After hours) It is the main drive (This server only had one drive partioned into 2) I am hopeing it will boot from it and just redect the new hardware on the new board. Hopefully only the network card will need adjusting 
 
Thanks

---

### Post by P4man on 2009-09-03
If you used binary video drivers, or a non standard disk controller (like a raid controller) you might run into troubles, but other than that, ive moved ubuntu installs  across vastly different machines with no problems.

---

### Post by patdundee on 2009-09-07
Hi Guys
 
Well that was a successfull move. The old system had Ubuntu Server with everything installed on an IDE drive but the replacement server was a SATA drive
 
I did a disk image of the two partitions (the ext and the swap) from the IDE direct onto the SATA (that took a couple of hours) I then placed the SATA back in the new server which was a completely different board, network and chip etc. The old drive went back into the old system undamaged. I then started the new server and everything seems to have booted up fine. 
 
That definately is a lot better than trying to do that with a windows box
 
Thanks for your help and advice much appreciated
:)

---

