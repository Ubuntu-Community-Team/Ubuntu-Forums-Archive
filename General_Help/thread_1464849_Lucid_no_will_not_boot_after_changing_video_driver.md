---
title: "Lucid no will not boot after changing video driver"
date: 2010-04-28
forum: General Help
---

### Post by bmillham on 2010-04-28
I'm running Lucid (all updates) with an ATI Radeon 3100 video ini a Toshiba Laptop.
 
I was troubleshooting a problem with XBMC, and tried disableing the propriatary ATI driver. Now ubuntu will not boot. I've tried recovery mode, and it gets to:
 
```

Begin: Running /scripts/init-bottom ...
Done.

```
 
and nothing else. I've tried CTRL-ALT-F1 and BACKSPACE, and nothing happens. I know that I just need to re-enable to ATI driver, or possible reconfigure X, but I can't figure out how at this point.
 
Hopefully oneone can help :-)
 
Brian

---

### Post by bmillham on 2010-04-29
No ideas on this one???

I found some info about booting a live CD, and using chroot. Is there any other way?

---

### Post by Mark Phelps on 2010-04-29
Don't know if this will help, but the link below shows how to remove the fglrx drivers using the console:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")  

If you do that, when you reboot, Ubuntu should automatically load the open-source drivers.

---

### Post by bmillham on 2010-04-29
> **Mark Phelps said:**
> Don't know if this will help, but the link below shows how to remove the fglrx drivers using the console:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  

If you do that, when you reboot, Ubuntu should automatically load the open-source drivers.
Thanks, I'll give that a try, if I can manage to get to a command prompt.

---

### Post by bmillham on 2010-04-29
I'm still unable to get my system back up.  Here's what I've tried:
 
Using e from GRUB to edit boot and added single to the boot. No luck, stops booting at the same spot.
 
Tried booting the LiveCD, and using chroot (to the broken installation) to remove the ATI driver and install the radeon driver. Same problem.
 
Tried booting the LiveCD again, chroot again, and re-enabled the proprietory driver. Still no luck...
 
I don't know what else to try, other that re-installing.
 
It's annoying that a simple disabling of a driver can make a system completely ususable. I can't belive that I can't even get into single user mode...
 
Any other idea???
 
Thanks, Brian

---

### Post by brk3 on 2010-05-29
> **bmillham said:**
> I'm still unable to get my system back up.  Here's what I've tried:
 
Using e from GRUB to edit boot and added single to the boot. No luck, stops booting at the same spot.
 
Tried booting the LiveCD, and using chroot (to the broken installation) to remove the ATI driver and install the radeon driver. Same problem.
 
Tried booting the LiveCD again, chroot again, and re-enabled the proprietory driver. Still no luck...
 
I don't know what else to try, other that re-installing.
 
It's annoying that a simple disabling of a driver can make a system completely ususable. I can't belive that I can't even get into single user mode...
 
Any other idea???
 
Thanks, Brian

Hi Brian,

I had the exact same problem, though it seemed to occur from installing xmbc, I didn't (to my knowledge) disable any drivers.

The way I fixed was the two following things, not sure which one did the trick (probably the second one).

Boot live cd and chroot.

- ran apt-get upgrade
- ran apt-get install --reinstall gdm mountall as seen here: [http://ubuntuforums.org/showpost.php?p=9054844&postcount=25](http://ubuntuforums.org/showpost.php?p=9054844&postcount=25)

Hope it works out for you if you haven't solved already.

---

