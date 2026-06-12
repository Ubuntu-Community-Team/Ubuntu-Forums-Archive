---
title: "Reloading Ubuntu"
date: 2010-11-25
forum: General Help
---

### Post by dual-boot on 2010-11-25
Hello to all, new member here.  I began using Ubuntu about 4 months ago and all has been well until recently when my screen began to freeze up every so often.  The problem initially only occurred every hour or so but has progressed to every few minutes.  I am not certain what happened but I did use a usb drive that had a virus from a Windows pc.  I was told by a Linux user at work that it wouldn't hurt my Linux OS.  I wanted to at least burn the data from it to a cd, which I did successfully, but ever since my computer has had the problem.  However, the problem is not the same as what the USB stick did to my Windows laptop, which it flooded with internet advertisements and eventually led to a blue screen and crashed my computer.  

With that said I would like to know the best way to reload Linux on my laptop.  I run a dual boot with Windows 7 and would like to keep it that way.  Do I need to reload Linux over top of the current installation or do I need to completely repartition my drive and reinstall it that way.  If the latter is the case, how do I go about that?  Do I simply expand the hard drive back to its original size and then shrink the space needed again and reload it?

Any help will be greatly appreciated.

---

### Post by sikander3786 on 2010-11-25
Welcome to the forums :-)

I would go for a clean install.

And in order to do that, just boot from your Ubuntu disc/USB and select Manual Partitioning and then the same partitions on which Ubuntu was previously installed. Don't forget to select them for format by ticking the small box in front of them. And don't format any other partitions by mistake.

You don't need to expand/shrink all those partitions again.

If you've got a separate /home partition, don't format it.

---

### Post by dual-boot on 2010-11-25
Thanks for the prompt reply.  I will do that now.  So basically you're saying the boot disk will take care of the formatting by performing a fresh install over the current one.  I thought that might be the answer but worried that it would create another partition.  I assume that will not be the case.

---

### Post by sikander3786 on 2010-11-25
> I thought that might be the answer but worried that it would create another partition.

It shouldn't create a new partition unless you advise it to do so.

Select your existing / partition, Edit it. Select mount point '/' (it should be already selected) and then select it for format.

Unless you define mount points for other partitions (which you shouldn't do) or prompt the installer to create new partitions, it shouldn't touch anything besides the '/' and swap partitions.

---

