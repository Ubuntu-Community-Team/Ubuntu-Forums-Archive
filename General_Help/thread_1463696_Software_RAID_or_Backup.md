---
title: "Software RAID or Backup?"
date: 2010-04-27
forum: General Help
---

### Post by chowder on 2010-04-27
I'm building a play server w/desktop at home, and want a backup solution.  I really like Time Machine for Mac and that does seamless backups my main machine onto an external HD or over a network drive.

For my server, is it better to use software raid (and get another internal HD) or use backup software.  Back up in Time: 
[http://backintime.le-web.org/](http://backintime.le-web.org/) 

seems like the most "time machine" type solution.  What's the difference between raid and regular automatic backups?  I'd like the most seamless automated solution.  

Thanks

---

### Post by davrosuk on 2010-04-27
I wouldn't rely on software RAID as any kind of backup. If you want to mirror drives its worth getting the hardware to do it properly - but this shouldn't be construed as a backup either in the technical sense (two drives can fail at the same time - its rare, but it has happened to me) But it also depends on how much you value your data of course :-)

---

### Post by chowder on 2010-04-27
It's nothing mission critical.  But still, I like my data.
What's wrong with software raid?  I didn't want to get a raid controller cause they are so expensive.

---

### Post by epsolon77 on 2010-04-27
A true backup needs to be on a different hardware set and location.  That's why you are being told not to do a local backup.  This is true.  If you want to keep your data, don't do it on the same hardware set.

Raid does not need to be expensive.  MDADM is a software raid package for linux that allows you to make a raid set without raid controllers or even two matched drives.

However, it sounds like you want incremental snapshots so you can roll your install back a few days if you screw up any kind of config.  You don't need to do this as a unique backup.  I would get a huge hard drive, at least 3 times larger than your primary (or the most you will put on the main hard drive) and run snapshots of that drive with something akin to RSYNC.  

I have been playing with OpenFiler, which will automate the snapshot system and raid setups quite a bit, but this would be on a separate box and likely larger than you are looking at.

Am I on the right track to your original intent?

---

### Post by yota on 2010-04-27
RAID mostly enhances service continuity, but is not a proper backup.

For instance it doesn't protect you from disasters like "rm -rf / tmp/*" (in which a misplaced space would lead to deleting *everything* instead of cleaning temporary files).
Also a RAID solution is not able to bring back to the yesterday-was-working configuration.

Bottom line: a real backup is always needed.

This is not meant to bash RAID which gives several other advantages (like recovery speed when an unit fails, performance improvements and so on).

p.s. when I say "RAID" I mean real redundant arrays (i.e. 0+1,1,5,6) and not 0 which should have been called "AID".

---

### Post by chowder on 2010-04-27
> **epsolon77 said:**
> A true backup needs to be on a different hardware set and location.  That's why you are being told not to do a local backup.  This is true.  If you want to keep your data, don't do it on the same hardware set.

Raid does not need to be expensive.  MDADM is a software raid package for linux that allows you to make a raid set without raid controllers or even two matched drives.

However, it sounds like you want incremental snapshots so you can roll your install back a few days if you screw up any kind of config.  You don't need to do this as a unique backup.  I would get a huge hard drive, at least 3 times larger than your primary (or the most you will put on the main hard drive) and run snapshots of that drive with something akin to RSYNC.  

I have been playing with OpenFiler, which will automate the snapshot system and raid setups quite a bit, but this would be on a separate box and likely larger than you are looking at.

Am I on the right track to your original intent?

Correct, I like the ability to take snapshots and roll back if necessary.  
That pretty much answers my questions/concerns, I'll go with regular backups.

Thanks!

---

### Post by epsolon77 on 2010-04-28
I like the idea of re-terming raid 0 to aid...That's a great thought.

---

### Post by Steven_S on 2010-04-28
I know it is solved, but this might still help: [http://www.smallnetbuilder.com/content/view/30060/79/](http://www.smallnetbuilder.com/content/view/30060/79/)

The reason I decided against RAID myself is that I want to be able to switch the drives in another system if things would go really wrong. That is a lot more feasible with mirroring drives (and yes, please do off-site backup of the most important files).

---

### Post by epsolon77 on 2010-04-28
Steven_s, I don't disagree with what you said but I do feel this needs more clarification.

"Backups" are not a singe solution.  I run 7 servers for a small company, and we have RAID and snapshots placed on tape (not happy about it but it's better than nothing).  There are many layers to backing up your system for a full commercial application and it's important to understand where technologies fit into each phase.  The OP seemed focused on a very narrow aspect of backups for a test system, so I didn't go into this further.  But I don't want people getting the wrong impression and skipping RAID.

RAID is great to real time fault tolerance.  This is why I like the idea of RAID 0 being called AID.  It's only benefit is speeding the drives.  RAID's purpose is to allow you to bridge physical hardware failure without needing to take the machine down, or at least without losing up time during peak hours.  So when your hard drive fails, your server can keep running until your acquire a new drive, or have the availability to shut your server down to replace the drive if you can not hot swap it.  This is not a backup in the conventional sense.  You are preventing failure that would require the use of your backups, so you are limiting your need for a backup.  The fact that you gain performance on thing like raid 5 and 10 or 0+1 is nice, but not why you use RAID.

A true backup is taking your data, or snapshot of your drive and moving it to a physical media that would not be hurt if something were to happen to your original.  So moving snapshots to a separate hard drive located inside the same computer is a backup that is tolerant of local hard drive failure, but not of a large surge or fire for instance.  Backing up just to a tape and leaving the tape onsite on the shelf is tolerant to anything short of a physical event in the server room like fire or emp pulse.  The systems I am looking at upgrading too involve moving all data to a hard drive bank with RAID backups and passing the data across sites to a similar system in another part of the state.  This would mean all my data is stored on a RAID array, but would be located in it's entirety on no less than 4 hard drives spanning two locations.  So in essence I could simultaneously lose 3 hard drives, and have a massive physical event, like fire, terrorism, nuclear bomb, in one location and still be LIVE with the data in the second location.  

So in short, local RAID a backup does not make, however RAID is a very important part of your disaster recovery and backup solutions.

---

### Post by epsolon77 on 2010-04-28
> **epsolon77 said:**
> like fire or emp pulse.  


Ok sorry, got a major call out from a friend.  There is no such thing as an EMP Pulse.  Thank you Wolfskin75 for correcting my egregious mistake.

---

### Post by Steven_S on 2010-04-28
I totally agree with that. I just approached it from a home user perspective - perhaps presumptuous of me. 

When I built the machine I am using now from old parts (you'd be amazed how nice and cheap things there are in shops that take back "worn out" office materials), it was intended to be a home and backup server. I took quite some time looking into the pros and cons of RAID. For my purposes, that is to say. The machine is not always on, and doesn't need the permanent availability RAID can offer. It just needs to collect data from the laptops in the house, so that a crash doesn't mean disaster. What made me decide even against RAID 1 or 0+1 in my situation is that - from what I gather - data availability is not always guaranteed (apparently rebuilding the RAID can take quite some time), and that you can't just swap out a drive and put it in a non-RAID machine. 

So now, after extensively looking at all sorts of NAS'es, I have filled a box with 3 1TB storage disks and an 80GB OS disk. The second mirrors the first, and the third was more a story of plans being bigger than data needs :-). Not to mention a now redundant old 250GB Buffalo Linkstation (which will probably become a home theatre server) and two or three old hard disks that are lying around somewhere in a closet. Having storage separate from the OS also means that I can safely play around with Ubuntu, for example. 

If the place would go up in flames: my workfiles are around on the web, and my pictures (the most precious material possessions of me as a parent) are all in full quality on a paid Flickr account. It is never fool-proof, I know :-).

---

### Post by CharlesA on 2010-04-28
I've got RAID on my server at home, running rsync to external drives daily. I do a monthly backup to another drive that is stored in a fireproof safe. I don't have offsite backups yet, but this is working for me. :)

---

### Post by chowder on 2010-04-28
> **Steven_S said:**
> I know it is solved, but this might still help: [http://www.smallnetbuilder.com/content/view/30060/79/](http://www.smallnetbuilder.com/content/view/30060/79/)

The reason I decided against RAID myself is that I want to be able to switch the drives in another system if things would go really wrong. That is a lot more feasible with mirroring drives (and yes, please do off-site backup of the most important files).

Wow, I never thought of a RAID controller failing...
Offsite backup is where it's at.

---

### Post by epsolon77 on 2010-04-28
> **chowder said:**
> Wow, I never thought of a RAID controller failing...
Offsite backup is where it's at.

My issue with RAID controllers are that they CAN fail.  That in and of itself is a major issue for me.  Hardware failes.  Software RAID, but that mesure are better.  They do take up clock time though which can get tricky.  As I said before I'm moving to an OpenFilier type system that allows me to store snapshots on a RAID setup that is SOLEY used as the RAID controller, and then the data is replicated on another OpenFiler box.  This means two RAID controllers with your data. It's way too much for a simple home system, but is right along the lines of the Dell Equilogic Boxes which are great for business high availability solutions.

Steve_S Thanks for understanding that I was trying to correct for a larger range of potential viewers.  Your conclusions are dead on for some home based applications.  While I wouldn't consider a $2000 RAID controller for home use, I'll look into more memory and a better proc to use a Software RAID selection off the stable linux kernel (Please dear GOD don't use Windows' Soft RAID.)  If you have two good hard drives and want to play with RAID, I very much recommend MDADM.

---

