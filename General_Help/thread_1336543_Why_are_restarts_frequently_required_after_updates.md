---
title: "Why are restarts frequently required after updates"
date: 2009-11-24
forum: General Help
---

### Post by w7hd on 2009-11-24
As a Linux user since 1995, I'm noticing a very disturbing trend.  Most of the time after I have installed updates, a restart is required.  This is very Windows-like activity, but is it really required?  I took pride in the fact that a restart was ONLY required for hardware upgrades/changes.  Apparently that has gone away.  Can anyone tell me why or is this one of those "groupie" things?

---

### Post by lykwydchykyn on 2009-11-24
As far as I know, they're only required for kernel updates or possibly updates to proprietary drivers that require a reboot to reload.

Have you been prompted to reboot for something other than a kernel update?

---

### Post by camaron1 on 2009-11-24
> **w7hd said:**
> As a Linux user since 1995, I'm noticing a very disturbing trend.  Most of the time after I have installed updates, a restart is required.  This is very Windows-like activity, but is it really required?  I took pride in the fact that a restart was ONLY required for hardware upgrades/changes.  Apparently that has gone away.  Can anyone tell me why or is this one of those "groupie" things?

I find estrange what you say as it doesn't happen to my at all. I think I've only have to restart once since 9.10 upgrade (kernel upgrade), maybe one more time (but I don't think so)

---

### Post by NFblaze on 2009-11-24
Smae here, I've only needed to restart with kernel updates and maybe hardware driver updates.

---

### Post by t0p on 2009-11-24
Yep, I agree with the consensus: the only time I notice a need to restart is if the kernell has been updated.

I suggest that the OP looks at what packages are being updated.  Then he will have a better understanding of why a restart may be required.

---

### Post by phillw on 2009-11-24
Had 2 boots. One when I finished the 9.04 -->  9.10 update, and one today for the new kernel - other than that... not been asked. Kernel updates are the only ones that should need a boot.

I've never had a driver ask me for a re-boot, but I may not have those drivers installed. Do post what update you're doing that causes a request for a re-boot.

Regards,

Phill.

---

### Post by gradinaruvasile on 2009-11-24
There are some programs that ask for reboot, for example changing network-manager to wicd - in that case it is nor necessary at all. I remember some other occasions, but not the names. Most of the time is enough to start/restart services, load/unload kernel modules.

I had Jaunty running for 60 days without restart and it was running very well - it did bug me with that notification though.

---

### Post by w7hd on 2009-11-30
It is usually after (yet another) kernel upgrade.  I guess it seems so frequent because I have so many machines running Linux in some variety and kernel upgrades seem to be occurring more and more often.  Also, since most of the machines are behind a firewall and normally don't connect to the Internet, they only get updated once a month.  

Question answered, though.   Thanks, guys.

---

### Post by Leppie on 2009-11-30
You may want to have a look at [Ksplice's Uptrack]("http://www.ksplice.com/uptrack/").

The only thing is that it's available just for Jaunty and Karmic.

---

### Post by w7hd on 2009-12-06
Actually, I tried Ksplice, but got errors under Karmic (Ubuntu 9.10 is definitely broken - won't work with wireless on my netbook or laptop).  Works okay under Jaunty.  No go for Redhat yet (darn), since that's what my servers run.

Anyway, I'll keep watching Ksplice to see if it appears on the Ubuntu updates - then it'll be worth using.

---

### Post by wdaher on 2009-12-08
@w7hd: Sorry to hear that you had some errors -- we'd be happy to take a look at the the problem to see what's wrong. Can you send us a copy of the error message, as well as the output of  /var/log/uptrack.log, to support@ksplice.com?

Thanks!
Waseem

---

### Post by SuperSonic4 on 2009-12-08
Often they don't need a reboot - since ubuntu is largely appealing to people just starting on linux it is easier to tell someone to reboot than to drop to a tty and manually reset the network/gdm etc....

Also you don't have to reboot,even for the kernel. It just means you won't be on the new version until you do

---

### Post by slakkie on 2009-12-08
New kernels require a reboot and network-manager also requires one, although the latter is not strictly needed, restarting the service is sufficient. 

NM doesn't restart itself after an upgrade because they (devs) don't want to break a wifi connection or ssh connections (for remote upgrades). That is why they want you to reboot, but again, this is not needed in normal situations.

---

