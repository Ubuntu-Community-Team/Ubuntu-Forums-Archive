---
title: "Just formatted HDD and installed Ubuntu... A very important question."
date: 2010-02-16
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-16
I originally tried Ubuntu 9.10 via a windows installation through Wubi. I had a VERY complex problem with a "Kernal Panic" due to an update through update manager and my system would not run proficiently. I wanted to know if that bug was exclusive to Wubi installations or does it also exist with this method of installation. I would greatly appreciate and help. I'm not going to update ANYTHING until I know for sure.
Regards;
CJ

---

### Post by x33a on 2010-02-16
Kernel panics happen due a lot of reasons, and are not related just to a wubi install. You can experience kernel panics on a full-dedicated install also.

Also, updates are very important to keep your machine running safe and stable. Though, sometimes updates do bring problems, but disabling them altogether is not the right solution.

---

### Post by CharlesJWelsh on 2010-02-16
I am aware of that. However that bug (to my knowledge) Was strictly native to Wubi installations. I was only trying to make sure before I do the updates.

---

### Post by bwhite82 on 2010-02-16
Its very hard to tell what it is related to. As mentioned already, there are a myriad of reasons for a kernel panic. Did you copy the panic message down and try googling? We have nothing to go by to help you otherwise.

---

### Post by CharlesJWelsh on 2010-02-16
Okay. I DID research on it. And it turned out to be a bug. Native to Wubi. I had to download a patch and everything. I had to replace "wubildr" with another "wubildr" (patched version) and I had to manually boot my computer from a sh:Grub menu. I just wanted to be SURE that this problem does not and will not affect the full installation of Ubuntu. I will have NO way to repair it because my ONLY OS is Ubuntu. I remember the message. I saw it so many times.

"kernel panic not syncing vfs unable to mount root fs on unknown-block 8 1"

Any help would be appreciated.
Regards;
CJ

---

### Post by GreyWizzard on 2010-02-16
> **CharlesJWelsh said:**
>  I will have NO way to repair it because my ONLY OS is Ubuntu.

Actually, having your only OS as Ubuntu would make fixing it easier.  Sure, you would have to do some research and learn to use the rescue CD and some basic command line, but the flexibility of Linux in this aspect is incredible.

I don't know what version of Ubuntu you downloaded and installed, but I have had my system going for several weeks now (and even longer if you include the time I tested it in VirtualBox on my previous OS) and I have installed every update I could find.  So far I have had ZERO kernel issues and I don't expect any either.

---

### Post by x33a on 2010-02-17
> **CharlesJWelsh said:**
> I just wanted to be SURE that this problem does not and will not affect the full installation of Ubuntu. I will have NO way to repair it because my ONLY OS is Ubuntu. I remember the message. I saw it so many times.

You should always keep more than 1 kernel installed, so that you can fallback to the older and tested kernel in case a newer kernel gives you problems.

---

