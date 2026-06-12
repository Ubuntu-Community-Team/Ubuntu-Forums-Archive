---
title: "Increasing partition with dual system"
date: 2010-03-25
forum: General Help
---

### Post by Benbow on 2010-03-25
For practical reasons I use Ubuntu and XP on the same 500gb hard drive. The drive is split into 5 partitions with just one dedicated to XP. My problem is that I have almost filled up the 100gb XP partition and I need to increase it by using some space currently used by Ubuntu. 
Can I do this from Ubuntu? or must I reformat the whole drive and reinstall XP followed by Ubuntu. My preferred method would be to increase the XP partition, but can I?
I am not too technical and anything which involves the command line is very difficult. I have persevered and used Ubuntu for four years so I am living proof that you don't often need the command line to use Linux successfully!

Thanks for any advice.

---

### Post by Paddy Landau on 2010-03-25
You can easily reduce Ubuntu's partition size using GParted (it's in the System > Administration menu, but you need to boot from a Live CD because your partition mustn't be mounted).

You can increase a Windows partition using GParted, but... GParted has been known to cause problems with Windows installations!

I don't remember XP too well. If XP has a native application to increase the partition size, then use that one to increase the Windows partition. If not, you may find a free application on [download.com]("http://download.cnet.com/windows/") to do it.

You can use [CloneZilla]("http://clonezilla.org/") to back up your partitions beforehand, just in case. You'll need sufficient space somewhere else (e.g. an external hard drive) for that.

I presume that you've used [CCleaner]("http://www.ccleaner.com/") to clean up your XP drive?

---

### Post by philinux on 2010-03-25
I just shrank an XP partition with gparted from the livecd. 

You must clean up, defrag then run checkdsk on XP first. And of course backup anything important.

XP hasn't got a built in partitioning tool. Gparted worked a treat for me.

---

### Post by Sin@Sin-Sacrifice on 2010-03-25
> **philinux said:**
> I just shrank an XP partition with gparted from the livecd. 

You must clean up, defrag then run checkdsk on XP first. And of course backup anything important.

XP hasn't got a built in partitioning tool. Gparted worked a treat for me.

Really?? My XP did... just went to 7 though.

---

### Post by philinux on 2010-03-25
> **Sin@Sin-Sacrifice said:**
> Really?? My XP did... just went to 7 though.

I couldn't find the damn thing. I think most peeps used third party apps for this.

---

