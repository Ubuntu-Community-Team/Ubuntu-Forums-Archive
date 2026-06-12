---
title: "hfs+ support"
date: 2010-10-14
forum: General Help
---

### Post by kr651129 on 2010-10-14
Is there a kernel for ubuntu that has hfs+ support built in?

---

### Post by coffeecat on 2010-10-14
Yes, the one you're posting from. :wink:

Problem is, if you have the journalled version of hfs+, you can only read a hfs+ filesystem. If you have a non-journalled hfs+, then you can read-write. But you may have permissions problems writing to the root of the filesystem if you don't invoke root powers or do a bit of chown-ing or chmodding.

By the way, someone may tell you that you need the apps hfsplus, hfsprogs and hfsutils that are in the repository. You don't - not to simply read and write files. I've just formatted a pen drive with the non-journalled hfs+ in my Mac and Ubuntu is reading and writing to it happily without those apps installed. (With a little permissions hiccup at first.)

---

### Post by kr651129 on 2010-10-14
Okay, I guess I should have been more specific.  Im building a linux distro from the linux from scratch project and I'm messing around with diffrent ways of installing it.  I'm trying to install linux on an HFS+ partition and mess around with some stuff under that.

---

### Post by coffeecat on 2010-10-15
> **kr651129 said:**
> I'm trying to install linux on an HFS+ partition

An original project. :-k Can I ask why?

---

### Post by kr651129 on 2010-10-15
Well for two reasons, neither of which being good enough to do something like this but they are what they are lol.

1. To learn more about the interworkings of linux
2. I'd like to make a linux distro that when installed side by side with mac can talked to each other easier out of the box, I'm also working on getting mac programs working smoothly under linux so I can kinda make a hybrid windows, linux, mac machine.

---

### Post by coffeecat on 2010-10-15
Good luck! :-s

:)

---

### Post by kr651129 on 2010-10-15
> **coffeecat said:**
> Good luck! :-s

:)

hey thanks!  If you want I can keep you updated on the progress.  I may even start a new thread if people want to help out with this hybrid project.

As for my next question; Has anyone here installed linux using GUID instead of MBR?

---

### Post by coffeecat on 2010-10-15
> **kr651129 said:**
> As for my next question; Has anyone here installed linux using GUID instead of MBR?

Not personally, but [it seems you can]("http://en.wikipedia.org/wiki/GUID_Partition_Table#OS_support_of_GPT").

---

### Post by kr651129 on 2010-10-15
> **coffeecat said:**
> Not personally, but [it seems you can]("http://en.wikipedia.org/wiki/GUID_Partition_Table#OS_support_of_GPT").

Sweet, I'll need to play with that when I get home from work!  Thanks again.  I hate finding out information that could be fun while your at work, you have the rest of the day to wait to get home and mess around with it all.

---

### Post by corbo950 on 2010-10-16
Hello, I would be interested in any help you need with your distro and I also would love you know how you get HFS+ support working as I currently have a external hard drive that is formatted as such so that Windows, Linux and Mac can read it. Also you might want to base your distro on BSD instead of linux as that is what OS X is built on.... that way you could reuse some of the Darwin code. Apple tends to hold back Darwin for release I believe the current version relates to 10.4(AKA Tiger). Anyway good luck

---

### Post by kr651129 on 2010-10-18
> **corbo950 said:**
> Hello, I would be interested in any help you need with your distro and I also would love you know how you get HFS+ support working as I currently have a external hard drive that is formatted as such so that Windows, Linux and Mac can read it. Also you might want to base your distro on BSD instead of linux as that is what OS X is built on.... that way you could reuse some of the Darwin code. Apple tends to hold back Darwin for release I believe the current version relates to 10.4(AKA Tiger). Anyway good luck

Sweet, thanks man I'll PM you my contact info

---

### Post by corbo950 on 2010-10-22
Sent you an email.... I have been looking at something called Adeos I'm thinking it might be possible use this to run the PureDarwin and Linux Kernels side by side and then write a Operating environment that would run on-top of both and manage all the things that would need to run on-top of both and then direct programs to the correct kernel depending on what they are(hate to describe it this way but the same way that Windows 95 was just a Operating environment running on-top of MS-DOS) Somewhat inefficient compared to either kernel normally but the point is to be more efficient then just running Linux and OS X side by side right? which this difficulty would be. Let me know what you think

Corbin

---

