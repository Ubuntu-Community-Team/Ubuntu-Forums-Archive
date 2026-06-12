---
title: "running windows under linux"
date: 2006-05-30
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-30
hey can ne1 tell me how to or give a link for a how to on running winodws under linux? i need it for some stuff plz ppl who dont want to help dont up ur post count by telling me i shouldnt need to use window setc etc etc just ppl whp are willing to help if u have ne insight.

---

### Post by badrinarayan on 2006-05-30
This [thread]("http://ubuntuforums.org/showthread.php?t=183209") should help you. Nobody here posts to "up their post count" - mostly they genuinely want to help.

---

### Post by FredB on 2006-05-30
There is another tool, called [Parallels Workstation]("http://www.parallels.com/"). It is installed the same way vmware does. But I didn't compare both to see which is the fastest one !

---

### Post by LORD_PoLvO on 2006-05-30
thnx for the help guys much appreciated

---

### Post by badrinarayan on 2006-05-30
May be you will like this [comparison]("http://en.wikipedia.org/wiki/Comparison_of_virtual_machines").  Parallels workstation is not free (as in beer). VMware is free and is also very easy to use. There are also GPL software like Xen and Qemu that are quite good.

---

### Post by dschaller on 2006-05-30
I run Windows 98SE inside Linux using QEMU ([http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)) with good success. I have had some trouble printing from within Qemu/Windows but I think that's due to a local networking issue on my end. All in all, QEMU is a pretty clever piece of software. It emulates the CPU so you can actually run a native Windows installation inside Linux. It's awefully funny seeing the blue screen of death captive inside a Linux window!

The faster your processor, the better QEMU will perform, of course. On my Sempron 2400+ I can run Win98 at near-native speed. I'm sure XP would be slower. Don't know what version you're trying to run.

---

