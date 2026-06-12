---
title: "Image Level &amp; Incremental Backups"
date: 2010-12-21
forum: General Help
---

### Post by jingaling on 2010-12-21
Hi Guys,

I am running Ubuntu on 3 machines at home and I am about to setup a 4th to act as a backup server - I will be installing Ubuntu Desktop as I don't need any of the LAMP systems as it's only going to be used for Backups really (and a spare machine from time to time).

At the moment I use De Javu (more info [here]("http://www.berthon.eu/ice_and_fire/?p=198")) for the backup of my home folders and CloneZilla for an image backup. What I would really like is something that can run image level backups and then regular incremental backups (i.e. only files that have changed) of my machines to the 'server'.

Acronis would be a Windows alternative. Is there anything like this out there? I have had a look around but they all seem to be either bootable live CD's or just folder level backups. If not, then so be it I'll will just stick with the system I have now.

Thanks in advance guys!

Jing.

---

### Post by VastOne on 2010-12-21
> **jingaling said:**
> Hi Guys,

I am running Ubuntu on 3 machines at home and I am about to setup a 4th to act as a backup server - I will be installing Ubuntu Desktop as I don't need any of the LAMP systems as it's only going to be used for Backups really (and a spare machine from time to time).

At the moment I use De Javu (more info [here]("http://www.berthon.eu/ice_and_fire/?p=198")) for the backup of my home folders and CloneZilla for an image backup. What I would really like is something that can run image level backups and then regular incremental backups (i.e. only files that have changed) of my machines to the 'server'.

Acronis would be a Windows alternative. Is there anything like this out there? I have had a look around but they all seem to be either bootable live CD's or just folder level backups. If not, then so be it I'll will just stick with the system I have now.

Thanks in advance guys!

Jing.

I use Grsync (gui front-end of rsync) over a ssh connection and it works perfectly... and is very fast... 

Note - you will have to supply the ssh port in Grsync advanced options/additional options.

PM me or respond here if you need additional information

---

### Post by jingaling on 2010-12-21
Hi Vast,

Thanks for the info. I am just building the new machine now - once I get to setting up the backups ill have a look. If I hit any snags I will PM you. Thanks for the help!

Jing

---

### Post by psusi on 2010-12-21
I suggest tar or dump.  The only advantage "image" type backups have is that you don't have to remember to restore the boot loader when you restore the backup to a blank drive, but they have several disadvantages.

---

### Post by jingaling on 2010-12-21
> **VastOne said:**
> I use Grsync (gui front-end of rsync) over a ssh connection and it works perfectly... and is very fast... 

Note - you will have to supply the ssh port in Grsync advanced options/additional options.

PM me or respond here if you need additional information

Hi Vast,

This isn't really what I am looking for. I want a tool that actually does physical backups - not just syncing my files to another place. Thanks for the help though!

---

### Post by VastOne on 2010-12-21
> **jingaling said:**
> Hi Vast,

This isn't really what I am looking for. I want a tool that actually does physical backups - not just syncing my files to another place. Thanks for the help though!

Once you do the initial "sync" or first time run, isn't that a backup?

and then the increment's follow?

I do hope you find what you are looking for.

---

### Post by jingaling on 2010-12-21
Thanks Vast,

It definitely is a viable option I am just looking for something a bit different. I would like my image and incrementals to be separate not just a daily sync.

After a bit of snooping around I think I have found what I am looking for in a tool called Simple Backup - looks really useful and can even send email alerts which I think is a brilliant tool!

I am in the middle of setting it up on my new machine now - will report back soon.

---

### Post by jingaling on 2010-12-21
Hey Guys,

This simple backup tool is exactly what I needed. It runs a full backup and then separate incremental backups. Perfect!

Thanks for your help on this guys, should have had more of a play around before posting really but hey, at least the info is now out there in case anyone else finds themselves in the same predicament as me.

---

### Post by jingaling on 2010-12-22
Hi Guys,

Just as a footnote to this thread. I have just had to do a restore from clonezilla and it went brilliantly didn't take very long at all and worked a treat! I am really impressed with clonezilla as a backup tool!

---

### Post by psusi on 2010-12-22
The problem with clonezilla is that it can not restore to a smaller disk than the original, and if you restore to a larger one, it does not use the additional space.  You also carry forward any fragmentation that was present in the original.  You also can not open the backup and pull out specific files that you may want to restore, without restoring the whole thing.

---

### Post by jingaling on 2010-12-22
Fragmentation is not an issue as it is a clean image just as I like ubuntu to be setup with no data (that's all held in ubuntu one). So I do not need any single files to come out of the backup.

I also have seperate images for each of my machines so I will only ever be restoring to the same hardware. The only time the hardware will change is if I upgrade, in which case I would restore, use gparted to increase the partition, install new drivers then re-image :).

---

