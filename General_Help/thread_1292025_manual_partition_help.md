---
title: "manual partition help"
date: 2009-10-15
forum: General Help
---

### Post by ShizzlePDX503 on 2009-10-15
alright so I used to have Windows Vista SP2 installed and made the switch to ubuntu after much testing it on a usb hard drive.

I booted to the cd to install ubuntu 9.04 and chose to configure partitions manually cause I wanted to only remove the Vista install and keep my factory recovery partition (7GB partition which was drive d:) in case I want to reinstall Vista again I will be able to.

so I removed the drive C: partition only and created a new partiton for the swap which I used 2048M since I only have 1GB of ram (laptop :( ). Then I created another partition for the / with 8192MB (ext3). Then another partion for the /home which was the remaining space which I think was like 89GB. The total drive is 120GB minus the 7GB for the recovery partition.

Now my question is did I leave enough space for the / partition, or is the home partition supposed to be smaller? Does it matter and if it does is it easy to fix? I just finished with the fresh install and the updates for ubuntu. Is there a general rule of thumb to follow when partitioning a harddrive?

Any input would be greatly appreciated. Thanks! Glad to be part of the ubuntu community.

---

### Post by justleen on 2009-10-15
8GB is enough for a root system, normally. my root partion is only taking up 3.1GB, and I tend to install whatever I like ;)

My self, I keep a smaller home partition, and have an extra partion for data (iso's, music, etc). But that is just personal preference.

---

### Post by DGortze380 on 2009-10-15
I like to have 10GB on root, but the system will certainly install and function with 8GB. Just watch that you don't fill up that space.

---

### Post by Niko Johnson on 2009-10-15
no i think your in good shape. it will still run with 8gb just make sure your not filling it up.. you shoud check frequently on how much space your using up, if i were you i would make a 20 gigs on / then the rest on /home. but it will still run, i dont know how much updates it can handle thoe or how much applications you can get without messing yourself up

---

### Post by az on 2009-10-15
I'm a fan of avoiding the problem completely and putting everything on one / partition (as is the default guided partitioning).

It's not that safe to keep a separate home.  It's easier to make a backup of your /home and reinstall.  If your drive dies, whether you partitioned it or not, your data is gone.  It's safer to make a backup on another medium.

Nowadays, with live CDs and cheap hard drives, there is no real reason for a separate home partition.

---

### Post by DeMus on 2009-10-15
> **az said:**
> I'm a fan of avoiding the problem completely and putting everything on one / partition (as is the default guided partitioning).

It's not that safe to keep a separate home.  It's easier to make a backup of your /home and reinstall.  If your drive dies, whether you partitioned it or not, your data is gone.  It's safer to make a backup on another medium.

Nowadays, with live CDs and cheap hard drives, there is no real reason for a separate home partition.

Can you explain that please:"It's not that safe to keep a separate home."
Why not? What is the real difference between a /home partition and a /home folder on the / partition?

---

### Post by az on 2009-10-15
> **DeMus said:**
> Can you explain that please:"It's not that safe to keep a separate home."
Why not? What is the real difference between a /home partition and a /home folder on the / partition?

Well, some people claim that having a separate home folder is safe in the event of a system crash.  Well maybe ten years ago, when there were no tools like live CDs available, you may have wanted to reinstall the / partition to be able to boot your computer up again.  But if your system crashed because your hard drive died, then you are lost.  

External drives are cheap these days.  Backing up to external drives are safer than creating a separate partition.  Not to mention easier/simpler.

The added advantage is that you run less of a risk of running out of space since the entire drive space is shared (home folder instead of home partition).  That is the topic of this thread;  to me, it's just not worth the effort.

My opinion.

---

### Post by ShizzlePDX503 on 2009-10-15
well I plan on getting this install of ubuntu all tweaked the way I want it with all the apps that I want then to save it to a dvd so I have my own personal ubuntu distro just for me. so that I don't have to keep installing the updates and drivers and all the software over and over. cause I know that I will end up breaking things and want to reinstall from the beginning. I am new to linux pretty much and I do a lot of searching on the web for things and its a way for me to learn a lot about it so that I can be comfortable with it and know my ins and outs. :)

---

### Post by ShizzlePDX503 on 2009-10-15
makes sense to me az and I may do that in a future install but for now I have to go with this setup for awhile.

---

### Post by Scunizi on 2009-10-15
I think az's reasoning is way off track.. because of the way the file system is accessed it doesn't care if /home is contained in the same partition as / or not.  However, placing /home in it's own partition is actually ease to back up with partimage or clonezilla.  It also affords some safety.  Even with a harddrive crash you may be able to retrieve your data if it's on a separate partition (your mileage may vary).  However as a new user of linux you will be doing lots of experimentation and most likely will mess something up that is beyond your fixing.  Having a separate /home makes reinstalling a snap while retaining your data.  

Typically the upgrade path from one release to another is pretty seamless for most.. I've never had that luxury.  I always reinstall fresh and leave my /home as is.. Upgrading in this way is important if you tend to use 3rd party repositories or have installed .deb's (programs) that have come from outside the official ubuntu repos.  

Just food for thought.

---

### Post by az on 2009-10-15
> **Scunizi said:**
> However, placing /home in it's own partition is actually ease to back up with partimage or clonezilla.  

It's just as easy to back up your home if it's a folder.

> **Scunizi said:**
> It also affords some safety.  Even with a harddrive crash you may be able to retrieve your data if it's on a separate partition (your mileage may vary).  

I do data recovery professionally.  That's false!

> **Scunizi said:**
> However as a new user of linux you will be doing lots of experimentation and most likely will mess something up that is beyond your fixing.  Having a separate /home makes reinstalling a snap while retaining your data.  

And as a new Linux user, it's easy to blow away your home partition while reinstalling....  Partitioning is probably the most complicated (and stressful) part of the installation process.

> **Scunizi said:**
> Typically the upgrade path from one release to another is pretty seamless for most.. I've never had that luxury.  I always reinstall fresh and leave my /home as is.. Upgrading in this way is important if you tend to use 3rd party repositories or have installed .deb's (programs) that have come from outside the official ubuntu repos.  


And if you install an earlier version of an app, the configuration files (from the later version) you have in your home folder may cause you problems.  Sometimes, you just need to flush out your dotfiles to fix a problem.

But hey!  To each their own.  I'm just saying it's simpler and less risky to put everything on the same partition.

---

