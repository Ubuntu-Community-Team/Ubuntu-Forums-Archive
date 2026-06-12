---
title: "RAID drive gone after upgrade"
date: 2011-04-27
forum: General Help
---

### Post by epud on 2011-04-27
I upgraded from 10.10 to 11.04 today and as a result my RAID drive no longer mounts. For me to be able to boot into Ubuntu now I have to skip the mounting processess if not the system just stalls.

It seems the RAID is still there but just not mounting correctly.

```
sudo dmraid -r
```

shows two discs at

/dev/sdd
/dev/sda

I would be grateful if anybody could help me with this?

---

### Post by epud on 2011-04-28
As far as I can tell the RAID system worked without mdadm. Any suggestions anyone?

---

### Post by epud on 2011-04-30
The RAID problem was fixed by an update.

---

### Post by erilidon on 2011-05-01
hmm... mine is not working. Had no issues with 10.10. However I have upgraded to 11.04 and now it wont show up. I have run all the available updates.

Any ideas on how to get my raid back?

---

### Post by epud on 2011-05-01
Yes, I should have been more specific.

I did an update which was suggested in this bug report. I got it working by:

```
sudo apt-add-repository ppa:psusi/ppa
sudo apt-get update
sudo apt-get install dmraid=1.0.0.rc16-4.1ubuntu4~ppa0
```

Make sure you update and restart making sure that:

dmraid and libdmraid1.0.0.rc16 gets installed.

Hope it works for you too!

---

### Post by a2j on 2011-05-01
both, my laptop and server are on software raid. working fine after an upgrade. using mdadm...

---

### Post by erilidon on 2011-05-01
> **epud said:**
> Yes, I should have been more specific.

I did an update which was suggested in this bug report. I got it working by:

```
sudo apt-add-repository ppa:psusi/ppa
sudo apt-get update
sudo apt-get install dmraid=1.0.0.rc16-4.1ubuntu4~ppa0
```

Make sure you update and restart making sure that:

dmraid and libdmraid1.0.0.rc16 gets installed.

Hope it works for you too!

No Go! I'm really not liking unity either. I think I'll just go back to 10.10. Thanks anyway.

---

### Post by JayDJr on 2011-05-16
I have searched the forums and this thread seems to most closely match my situation.  I have an Intel motherboard with on board RAID just like is described here, the only difference is that I boot from the RAID array!!!  When 11.04 boots up I get the boot manager window but as soon as I pick anything the bootup process fails, complaining that it can't find the boot drive.

Since I can't boot up the system, I can't run the apt-get commands referenced earlier.  Is there any hope of getting my system back or do I need to just fall back to version 10.10?

Thanks in advance for your help.


*** Jay ***

---

### Post by epud on 2011-05-17
Hi Jay.

I would think you would use a bootable USB or a CD to run Ubuntu live and fix it from there. What you would do exactly I do not know. I submitted a bug report and then my problem was solved. The place I submitted it, and the place where you will find the RAID experts are here: [RAID Bug Report]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/772483").

---

### Post by JayDJr on 2011-05-19
Thank you, this sets me on the path.  I will try these suggestions and maybe submit my own bug.  Much appreciated!
 
 
*** Jay ***

---

