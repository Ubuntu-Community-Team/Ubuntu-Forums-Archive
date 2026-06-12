---
title: "Filesystem Issues.. I think"
date: 2009-08-07
forum: General Help
---

### Post by jadhav333 on 2009-08-07
I have some kind of file system error.. I think..

The boot process gets stuck at 25%.. later it continues and drops down to a blue screen stating GDM doesnot work due to internal error..

I did a fsck in recovery mode.. it made some corrrections.. and rebooted. The GDM loaded and I was in.. 

Now 
a) It doesnot detect the lan card.. ( the networking icon doesnot show up in the tray) 
b) The command "Administrator > Hardware Drivers" do not work.
c) In the exit dropdown menu, the shutdown command is no longer there.

When I tried to fsck again.. it says to umount the partition.. if we (try to) umount it.. it says it is already unmounted.. if we try to run fsck.. it says it is mounted.. I am going loco.. 

Pls help.. I have tried reinstalling the system from scratch using a live cd and re partitioning all the partitions as well.. (twice /thrice)

I really cannot show any logs/screenshots as the m/c is my home machine.. and I am writing this from my office m/c.. I cannot bring data from home to office.. :)

---

### Post by jadhav333 on 2009-08-07
1) Also there was this following message in the boot log.. 

.... There appears to be no BMC in this location
.....
.....
.... PCI INT D is disabled


The dotted line indicates more messages.

Does this have to do anything with 'PCI INT D is disabled' or 'no BMC in this location'

2) Also, If I did a right click on any partition, and check the permissions tab.. it says that "the permissions of that particular partition could not be determined"

---

### Post by jadhav333 on 2009-08-07
After working overnight (without sleep) I managed to rectify the issue (which i think was the corruption of the file system and effectively the system files) by using sysrescue disk.. then I re-installed ubuntu.. and now everything seems to be in order.. I am keepng my fingers crossed though until I update all the patches.. restore the backed up data.. and install all th required programs.. i.e. have a fully functional system in hand..

---

