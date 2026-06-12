---
title: "Most stable Linux release for double-boot n00b"
date: 2011-03-10
forum: General Help
---

### Post by ZZalgern0n on 2011-03-10
Hi there,

I've been using WUBI for about 6 months, and it just crashed.  I saved it.  But in my searching, I saw many people recommend against using WUBI for stability.  In addition, I've noticed in my computer performance that Windows is hogging gobs of memory in running Linux, which takes away half the functionality here.  

What is the most stable way to get a version of Linux on here?  

I can undo WUBI and then should I go for a specific Ubuntu (or other version) release?  

And is it safe to put it on a separate partition?  

How much memory do you recommend setting aside for the Linux partition.  

Can I still access my Windows data through Linux if it's on a separate partition?  Many thanks!

---

### Post by howefield on 2011-03-10
> **ZZalgern0n said:**
> I've been using WUBI for about 6 months, and it just crashed.

Wubi is a good way to get to know Ubuntu in a fairly safe manner ie, without the perils of partitioning your drive. But I'd not recommend it for long term use. If you are happy enough to keep Ubuntu, I'd always recommend a "real" install. 

> What is the most stable way to get a version of Linux on here? 

Download from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and burn the iso image to a CD/DVD/USB.

> I can undo WUBI and then should I go for a specific Ubuntu (or other version) release?

You can uninstall the Wubi install via Add/Remove Programs or Programs and Features depending on the version of Windows that you are using.  

> And is it safe to put it on a separate partition?

It is arguably safer than a Wubi install. It is as safe as your Windows installation :)  

> How much memory do you recommend setting aside for the Linux partition. 

Do you mean hard disk space ?

As much as you want, I wouldn't go below 10gigs,  - maybe around 20 - 30 gigs - or more.
 
> Can I still access my Windows data through Linux if it's on a separate partition?

Yes, Ubuntu will read your windows data, but it won't work the other way round. If you need both operating systems to access the same data, try a separate partition formatted as ntfs, that way you Windows install won't be at risk.

Before you go ahead, just make sure that all valuable data is backed up elsewhere, in case you come a cropper. :)

Try some of the videos at screencasts.ubuntu.com where they show you how to dual partition, one caveat is that they may now be a little dated, but should still give you an understanding of the process.

---

### Post by ZZalgern0n on 2011-03-10
Great!  Thanks.  I was converted by an Ubuntu user who recommended against partitioning the drive.  

But I am more than happy with Linux in the long run.  I use it 99% of the time now.  However, there are a few Windows programs I can't do without, and WINE won't seem to port them without much difficulty (Photoshop, high-level video editing software).

Do you recommend the latest Ubuntu or is there another Linux release that is worth going after?

Thanks!

---

### Post by wiggly81 on 2011-03-10
gimp... it take a little getting used to but with plugins etc. you can run it as alternate to PhotoShop

---

### Post by ZZalgern0n on 2011-03-10
Thanks, I know about Gimp, but it doesn't fulfill my purpose.  It's lacking many filters for editing and doesn't even handle the RAW files that my camera takes.

---

### Post by lithopsian on 2011-03-10
If you're hooked on "windows" as in graphical interfaces to the system, icons, point and click, then stick with Ubuntu.  It is pretty stable.  Even more stable would be Debian and to be honest it is pretty similar.

If you're already hooked on Linux and like the way it operates then you could try a different distro.  Or try lots of them!  Just save yourself a 20GB partition and you can install lots of (free :)) Linux distros to see how they compare.  I like Crunchbang.

Don't get me started on Gimp!  It is easy to keep a dual-boot Windows around, at least for a few years, but slightly annoying to keep switching just for Photoshop.

---

### Post by ZZalgern0n on 2011-03-10
> **lithopsian said:**
> If you're hooked on "windows" as in graphical interfaces to the system, icons, point and click, then stick with Ubuntu.  It is pretty stable.  Even more stable would be Debian and to be honest it is pretty similar.

If you're already hooked on Linux and like the way it operates then you could try a different distro.  Or try lots of them!  Just save yourself a 20GB partition and you can install lots of (free :)) Linux distros to see how they compare.  I like Crunchbang.

Don't get me started on Gimp!  It is easy to keep a dual-boot Windows around, at least for a few years, but slightly annoying to keep switching just for Photoshop.

Good idea!  I should try a few out when I get a moment.  I am still a bit hooked on windows, as I haven't yet had the time to learn tons of terminal commands.  In a way, I enjoy whenever Linux crashes or doesn't act accordingly, because I have to learn more sudo commands and system architecture.  

I don't mind stepping up to the next level of "windows" but with a bit of extra brain work involved.  Maybe I'll try Debian!

---

### Post by howefield on 2011-03-10
> **ZZalgern0n said:**
> Great!  Thanks.  I was converted by an Ubuntu user who recommended against partitioning the drive.  

But I am more than happy with Linux in the long run.  I use it 99% of the time now.  However, there are a few Windows programs I can't do without, and WINE won't seem to port them without much difficulty (Photoshop, high-level video editing software).

Do you recommend the latest Ubuntu or is there another Linux release that is worth going after?

Thanks!

Absolutely nothing wrong with keeping windows around for keeping life sweet and easy when you need it.

There are 2 choices when deciding on which Ubuntu release to get, firstly LTS (Long Term Support) which is supported for 3 years on the desktop. Current LTS is 10.04 Lucid Lynx.

Then there are the non LTS editions which are supported for 18 months but may be slightly more current in term of kernel and application versions, but possibly ever so slightly more risky.

Ubuntu releases come around every six months, with certain versions designated as LTS, generally every 2 years.

---

### Post by Mark Phelps on 2011-03-10
When you're running Ubuntu using Wubi, you're not actually running "inside" Windows.  All you did was utilize the Windows boot loader (and GRUB4DOS) to boot into Ubuntu.  So, there is no way that Windows is using gobs of memory when you are running Ubuntu.

---

