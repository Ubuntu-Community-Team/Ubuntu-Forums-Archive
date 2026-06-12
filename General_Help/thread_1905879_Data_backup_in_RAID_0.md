---
title: "Data backup in RAID 0"
date: 2012-01-07
forum: General Help
---

### Post by Sompom on 2012-01-07
Hello everyone-
I'll cut right to the chase here. One of the disks in my RAID 0 array is showing bad sectors and is making bad noises. I believe that both disks are still in warranty, so I'm hoping to just get with the manufacturer and replace them(either of my laptop or of the disks, if MSI tells me to stuff it up my a-hh-- bum). The problem is, I cannot just clone the data onto the new disks, because they are not yet in my possession, and I understand dd will not work unless the disk are exactly the same, which would require a good deal of luck. Does anybody have a better solution (just TAR every partition and unTAR them back onto the new disks, perhaps?). I have access to a big enough external drive, could I just use Clonezilla to clone the RAID array onto that, then put that somewhere safe until new drives arrive?
Thanks for any thoughts! :)
P.S. The drives read OK (for now), although Linux has ceased to boot (could be a coincidence? The drives only ever made noise while booted into Linux) I can boot a thumb drive to run any commands needed, and I have made no effort to restore Ubuntu.

---

### Post by rsvancara on 2012-01-07
I can not think of anything else you could possible do.  RAID0 is a ticking time bomb.  At least with a single disk, you can work around the bad sectors and get some of your data back.  RAID 0, once one disk is gone, it is pretty hard to get things back.

---

### Post by Sompom on 2012-01-07
I know >.< If I had thought about it before I got it all set up, I probably would have just gone with two separate disks because I really don't notice a speed difference and it's quite a huge gamble... Oh well... I suppose the advantage of the TAR method is I could change when setting up the new disks!

---

