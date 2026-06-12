---
title: "boot splash problem"
date: 2011-05-17
forum: General Help
---

### Post by linkinsebas on 2011-05-17
I've been having an ugly ubuntu boot splash for several months instead of the regular one. It looks like it changed after installing the ATI drivers. I am using Ubuntu 10.10 x64. It looks like it is a classic problem with  well-known solutions. HOWEVER, these solutions don't seem to work. For example, this one:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Also, the splash screen doesn't use the whole screen. A similar problem happened after login (and even using windows), but it was solved by modifying the "overscan" option to 0% in the ati configuration program. I thought this couldn't be solved for the splash screen, but when using ubuntu 11.04 (Live USB) this problem doesn't appear. Is there any way of correcting this for the splash screen? for the grub2 menu?

Thanks for your help.

---

### Post by Hedgehog1 on 2011-05-17
> **linkinsebas said:**
> I've been having an ugly ubuntu boot splash for several months instead of the regular one. It looks like it changed after installing the ATI drivers. I am using Ubuntu 10.10 x64. It looks like it is a classic problem with  well-known solutions. HOWEVER, these solutions don't seem to work. For example, this one:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Also, the splash screen doesn't use the whole screen. A similar problem happened after login (and even using windows), but it was solved by modifying the "overscan" option to 0% in the ati configuration program. I thought this couldn't be solved for the splash screen, but when using ubuntu 11.04 (Live USB) this problem doesn't appear. Is there any way of correcting this for the splash screen? for the grub2 menu?

Thanks for your help.

I have the same behavor on my ATI card on my office PC.  When I boot it off my Natty USB install, it uses the full 1920x1200.  But when I had 10.10 on the USB, I had the 'little window'.

On my home NVidia based systems, I still get the 'little window' using the Natty USB.

The generic video support for Natty seems to support ATI better then it did for 10.10.

***The Hedge***

:KS

---

