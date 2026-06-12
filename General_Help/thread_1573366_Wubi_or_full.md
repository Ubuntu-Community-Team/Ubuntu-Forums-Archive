---
title: "Wubi or full"
date: 2010-09-12
forum: General Help
---

### Post by opasnost on 2010-09-12
Hi guys,

I'm deciding on how to install ubuntu 10.04 on my laptop but im a little caught up between using the wubi or full install heres my dilemma.

I like the wubi but it doesn't support hibernation and from doing some reading it is not as stable and has some loss in performance.

The main issue I have with doing the full install is I'm a little concerned that making new partitions may screw up the recovery partition which I find really useful which lets me easily reformat my laptop without having to deal with all the drivers.

So my real question here is twofold. Is there a way to still hibernate in wubi? And is the full install that much more stable and faster?

Second should the recovery partition be ok if i later decide to start fresh again in the future?

thanks in advance for suggestions help and advice.

---

### Post by Lateralis on 2010-09-12
I don't think I've ever tried the Wubi install, but there's a part of me that seems to be apprehensive about it.  I can't put my finger on it, but the thought of installing it as a directory within a Windows operating system just makes me nervous!  So I would say install the full shebang, but there are plenty of others which would advocate Wubi.  Ultimately, it is your decision and you have to make the one you feel most comfortable with.   

Supposing though that you wanted to install Ubuntu to you hard drive proper.  As When I installed Ubuntu on my (then newish) laptop a year ago, I was unaware of a recovery partition being on the disc - I only found that out when I got to the partition setup stage of the installation!  My recovery partition is perfectly fine and there's no reason to think that yours won't be.   

So, if you want to install a fresh copy then it should be safe to do so.  As I say, that's what I did and I've had no issues whatsoever.  

One thing I would say and recommend incredibly strongly with ever fibre of my being is to ensure you have a second NTFS partition in addition to your Windows system partition.  This is because Win 7 and Vista do not like other systems, i.e. Ubuntu, writing to them.  Moreover, the NTFS support in Linux is OK, but not foolproof.  It is therefore much better to read/write to a common "shared" partition which is *not* the Win 7 system partition.  

OK so my setup on my laptop is as follows:

sda1 - Win Vista recovery 
sda2 - Win Vista System partition 
sda3 - NTFS "data" partition
sda4 - Extended partition:
  sda5 - Ubuntu '/' partition
  sda6 - Linux swap partition

If you ever want to restore your laptop to "factory settings" then you can use the recovery partition and nuke the whole lot.  

Of course, before you install and make changes to your partitions, you should ensure you have a full backup of all of your important data on an external medium, such as USB thumb drive or external HDD or CD/DVDs.

---

### Post by Lateralis on 2010-09-12
[Ohhh, double post.  :-/ My bad]

---

### Post by wojox on 2010-09-12
Wubi was designed to try out Ubuntu. It's not for any long term use. So go ahead and dual boot for now or do a full install. 

> And is the full install that much more stable and faster?

Yes it is both faster and more stable.  ;)

---

### Post by Mark Phelps on 2010-09-12
> **opasnost said:**
> The main issue I have with doing the full install is I'm a little concerned that making new partitions may screw up the recovery partition which I find really useful which lets me easily reformat my laptop without having to deal with all the drivers.

Two thing to be careful of ...

First, go to the appropriate link below, download and burn a Vista repair CD.  That will prove invaluable later should you need to repair the Vista loader:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Second, use the Vista Disk Management utility to shrink your Vista OS partition to make room for Ubuntu. Then, select the "largest free space" option in Ubuntu.  Do NOT use the Ubuntu installer to shrink the Vista partition.

---

### Post by opasnost on 2010-09-12
> So, if you want to install a fresh copy then it should be safe to do so. As I say, that's what I did and I've had no issues whatsoever.

Did you ever perform a fresh install to "factory settings"?

I will take your advice on creating a separate NTFS data partition but would you mind letting my know a little more in depth why it is necessary or at least a good idea? For learning sake...lol

---

### Post by opasnost on 2010-09-12
> **Mark Phelps said:**
> 
Second, use the Vista Disk Management utility to shrink your Vista OS partition to make room for Ubuntu. Then, select the "largest free space" option in Ubuntu.  Do NOT use the Ubuntu installer to shrink the Vista partition.

Where and when do I come across this option? Do I get to that when installing alongside windows from the liveCD or???

---

### Post by opasnost on 2010-09-12
Would backing up the recovery partition lets say as an image on a DVD be a good idea?

---

