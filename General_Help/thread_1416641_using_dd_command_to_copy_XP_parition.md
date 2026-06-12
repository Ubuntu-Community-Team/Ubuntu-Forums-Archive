---
title: "using dd command to copy XP parition?"
date: 2010-02-26
forum: General Help
---

### Post by bertmanphx on 2010-02-26
[LEFT]Hello,
I'm upgrading my parents computer from SUSE 11.0 to Ubuntu 9.10.  The install will be on a new hard drive.  The logifle for zypper grew to 25GB.....and made it impossible to log into their user.  Consequently, they shipped it back to me for service :)

I can migrate their /home data OK, no problems there.

My question is:  Can I use the dd command to copy an entire partition that has a full install of XP on it, to the new drive with similar parition, then, after installing Ubuntu onto the other partitions, will GRUB pickup the XP install and allow it to boot?

I could just re-install XP, but I'd have to chase down all the drivers.  BTW, XP only get's used during tax season...(USA).  Other than that, they are converted to Linux 100%.

TIA,

bertmanphx
[/LEFT]

---

### Post by Dies on 2010-02-26
Yes, it should work just fine, I've done it many times.

There *may* be some gotchas, for example sometimes it's necessary to run a "check" on the restored partition using ntfsprogs or gparted if you like. 

Another thing I would suggest is restoring the partition then running "fixmbr" and "fixboot" from the install cd and making sure Windows is good to go before installing anything else.

---

### Post by bertmanphx on 2010-02-26
Dies,
Thank you for the tips....I'll try that!

bertmanphx

---

### Post by Mark Phelps on 2010-02-27
> **Dies said:**
> Yes, it should work just fine, I've done it many times.

There *may* be some gotchas, for example sometimes it's necessary to run a "check" on the restored partition using ntfsprogs or gparted if you like. 

Another thing I would suggest is restoring the partition then running "fixmbr" and "fixboot" from the install cd and making sure Windows is good to go before installing anything else.

+1 good points

One more thing ... presuming that XP does boot and run, don't be surprised if it suddenly deactivates itself.  I don't know what kind of license you have (i.e., retail, OEM, VLK), but in some cases, changing the OS hard drive automatically deactivates MS Windows.

I had that happen on one "move" but fortunately, since I had a retail license, I simply reactivated online and all was well.

---

### Post by louieb on 2010-02-27
I used Gparted ([SystemRescueCd]("http://www.sysresccd.org/Main_Page") ) a couple of times to copy the XP partition when I put in a bigger drive. 
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 

Re-Activation was hit or miss one time I had to - one time I didn't. 

XP did run chkdisk both times. 

Did not have to run fixboot or fixmbr. - 

Just another option.

---

