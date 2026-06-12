---
title: "Ran into a problem I have never seen before on a fresh install."
date: 2009-11-23
forum: General Help
---

### Post by cptrohn on 2009-11-23
My nephew was running windows, and had a very large amount of Malware/malicious software attached to his computer.. (illegal music and movie downloads I think)

So to make a long story short his parents had been dual booting with Ubuntu and told me to just put it on his computer... So I brought it home and popped in a LiveCD to see if things would work, and everything seemed good.. So I restarted and attempted to run DBAN to wipe the HD for a fresh install, and Dban started but finished with errors....

SO I removed the DBAN disk and put the 9.10 live CD back in and started to boot with it and this time instead of loading up I got a ```
kernal panic intid
``` message.... So I powered the machine down and tried a Gparted Live CD and then got an err2err3 message instead of the machine booting.......

I am running a disc check in bios right now to make sure the HD is ok, but I have never once had anything like this happen at all..

---

### Post by cptrohn on 2009-11-23
Is this a problem with the windows bootloader?

---

### Post by CharlesA on 2009-11-23
I doubt it. Sounds like a problem with the hard drive. If DBAN finishes with errors it means that the drive probably has some bad sectors on it. Try booting off a livecd and running fsck.

---

### Post by mechro on 2009-11-23
Your LiveCD and Gparted disk aren't using the Windows bootloader.

It sounds like a hard drive and/or optical drive problem.

If the hard drive has errors you might be able to fix it with a manufacturer's recovery tool.

---

### Post by cptrohn on 2009-11-23
> **mechro said:**
> Your LiveCD and Gparted disk aren't using the Windows bootloader.

It sounds like a hard drive and/or optical drive problem.

If the hard drive has errors you might be able to fix it with a manufacturer's recovery tool.

Maybe.. Geez I hope so anyway.  The disc check should finishing soon, so hopefully his HD isn't failing.. if it is then maybe I will just get him a new for christmas... (LOL Damn I am such a good uncle.. LOL)

---

### Post by Don1500 on 2009-11-23
Ya, drives are cheap.

---

### Post by mechro on 2009-11-23
For example, if it's a Seagate drive you can get *Seatools for DOS* on floppy or CD...

[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=201271](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=201271)

---

### Post by cptrohn on 2009-11-23
Ok well the Hard drive was fine.

Good call on the optical drive.... made a USB startup iso instead changed the boot order and it fired right up into the liveCD and is installing as we speak..... I'll have to try some different stuff on discs.... maybe my disc got corrupted...

Thanks for the help though guys... Much appreciated!

---

