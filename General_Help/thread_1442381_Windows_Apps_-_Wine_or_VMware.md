---
title: "Windows Apps - Wine or VMware"
date: 2010-03-29
forum: General Help
---

### Post by A4orce84 on 2010-03-29
Hey Everyone,

So I'm somewhat of a Linux / Ubuntu newbie and had possibly a "dumb" question.

I've been playing around with Ubuntu for the past few distributions and was wondering I guess why would it be better to use say Wine over VMWare (or vice versa) for windows application's that do not have a Linux equivalent?

I understand the appeal of VMWare (especially if you are dual-booting already) in the fact that you don't have to restart, but isn't it better to see if you can get those application's running somewhat natively in Ubuntu (Linux) ?

I guess I just wanted people's opinions and to hear the pros/cons on which is better.

Thanks in advance!

--Asif

---

### Post by Agent ME on 2010-03-29
Wine runs windows programs directly on your linux computer, while VMware runs windows programs on a virtualized windows system running on your linux computer, possibly with some hacks to make the virtual windows system look more like just another part of the linux system. Having a virtual windows system adds more overhead (cpu-wise and having to manage another system -wise) but sometimes is the only way to get certain applications to work fully.

Put another way: programs under Wine run faster, can access your linux user files directly, and have access to hardware like for 3d acceleration, but not all programs work with it. Running programs under VMware requires you to have a (virtual) windows install, jump through hoops to access your files under linux, and often have less direct access to hardware, preventing 3d acceleration, etc, but otherwise runs the windows program exactly as it would under windows.

Use Wine if you find that it works for your program.

---

### Post by A4orce84 on 2010-03-29
anyone else?

---

### Post by A4orce84 on 2010-03-30
Ttt

---

### Post by steev182 on 2010-03-30
Wine doesn't work with USB, so you'll need the proprietary version of VirtualBox or Vmware if you want to sync your iPod.

---

### Post by sandyd on 2010-03-30
> **steev182 said:**
> Wine doesn't work with USB, so you'll need the proprietary version of VirtualBox or Vmware if you want to sync your iPod.

no need to install virtualbox just to sync your ipod. wait a few weeks, and youll have native ipod support...

---

### Post by eriktheblu on 2010-03-30
I say use both. Wine is the preferred solution, but the Wine compatible programs are limited. Virtualization is more compatible, but comes at the cost of system resources and cannot fully utilize your hardware like the host OS could.

---

### Post by hardbeans on 2010-03-30
I agree. Wine uses less system resources, which can be good if you're computer isn't a super tricked out one. VM Ware requires that you install a Windows OS but Wine doesn't. You'll be doing more work to get VM Ware working from the start, it'll use more resources, but you'll basically have a complete and working copy of Windows that you can run side by side with ubuntu. Wine just runs what Windows apps it can. Sometimes it's a bid buggy, but for the most part it works fine.

---

### Post by Mark Phelps on 2010-03-30
To aid in your choice, go to the WineHQ link below and enter the name of the MS App you want to run, and click the Update filter button.

It will then show you the compatibility ratings for different versions of the MS app.

Platinum and Gold ratings mean is will work just fine. Silver means just OK.  Bronze means some things won't work.  Garbage means just that -- nothing you will do will make it work.

Virtual solutions don't have such ratings because, basically, most anything will install and work.

---

