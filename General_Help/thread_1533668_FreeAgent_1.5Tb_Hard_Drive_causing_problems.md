---
title: "FreeAgent 1.5Tb Hard Drive causing problems"
date: 2010-07-18
forum: General Help
---

### Post by ninjapirate89 on 2010-07-18
For some reason my external hard drive keeps mounting and unmounting itself resulting in this:
[ATTACH]163829[/ATTACH]
Anybody else have this problem?

---

### Post by ninjapirate89 on 2010-07-19
Bump. Does no one know how to fix this?

---

### Post by watupgroupie on 2010-07-19
My 1.5TB drive works just fine. Only problem I have is it uses a mini usb cable to connect and it easily comes out. Nothing to that affect though.

---

### Post by ninjapirate89 on 2010-07-19
> **watupgroupie said:**
> My 1.5TB drive works just fine. Only problem I have is it uses a mini usb cable to connect and it easily comes out. Nothing to that affect though.

Is it the same brand? A SeaGate FreeAgent.

---

### Post by watupgroupie on 2010-07-19
No it's a WD drive. Does your drive work well in any other OS's you use?

---

### Post by ninjapirate89 on 2010-07-19
> **watupgroupie said:**
> No it's a WD drive. Does your drive work well in any other OS's you use?

No, it does the same in Win 7. If I leave it alone for a while I'll come back to my computer and have several Explorer windows open.

---

### Post by watupgroupie on 2010-07-19
It's got to do with the drive most likely then. Make sure your cables are connected well. If it's still happening I'd say there is issues inside the drive with faulty connections.

---

### Post by ninjapirate89 on 2010-07-20
> **watupgroupie said:**
> It's got to do with the drive most likely then. Make sure your cables are connected well. If it's still happening I'd say there is issues inside the drive with faulty connections.

I'd considered it being a loose cable before but they were connected fine. I don't think it's likely to be a physical problem with the hard drive since it's fairly new (about 4 months old). 
I also thought it could be the O/S spinning down the disk when inactive but in Win7 I changed the settings so it wouldn't do that and it didn't help. I don't know how I could try this in Ubuntu though.
The only other idea I've considered is that maybe the drive itself has something built into it that spins it down when inactive.

---

### Post by watupgroupie on 2010-07-21
My drive doesn't have a feature to spin down by itself. The higher quality ones though mostly do. I did a little reading and people who said they had spin down issues had to use the configuration tool on Windows and set it to never spin down. They encountered issues when putting it on other settings.

---

### Post by ninjapirate89 on 2010-08-01
Bump. 
I found this page [http://alienghic.livejournal.com/382903.html]("http://alienghic.livejournal.com/382903.html") which says to use 'sudo sdparm --clear STANDBY -6 /dev/sdb' to fix it. It works but only until I restart or unmount the drive. Is there a way I can set this to run automatically whenever the drive is mounted?

---

