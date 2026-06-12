---
title: "screen is not composited - Kernel 2.6.28-16"
date: 2009-10-23
forum: General Help
---

### Post by r5r4y on 2009-10-23
Hello,
Yesterday I've installed some upgrades to my system, 2.6.28-16 was one of them...

when I'm booting into the system with this kernel I'm getting a error message about my screen isn't composited, desktop effects does not work and everything is very slow... 

I'm using HD4870 with the newest ATI Drivers (9.10) which already have support for 2.6.31 kernel...
If I'm trying to boot into 2.26.28-15 everything works perfectly fine...

When trying to run compiz from terminal this is the output:

```

compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

```

How to solve this?

---

### Post by P4man on 2009-10-23
I believe if you dont use the restricted drivers offered by the hardware drivers app, then you need to reinstall the drivers when you do a kernel upgrade. Or use [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") somehow.

In short, try booting the new kernel and reinstall catalyst drivers. There might be a command to recompile the kernel modules without reinstalling all of the drivers, but I dont know it.

---

### Post by r5r4y on 2009-10-23
> **P4man said:**
> I believe if you dont use the restricted drivers offered by the hardware drivers app, then you need to reinstall the drivers when you do a kernel upgrade. Or use [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") somehow.

In short, try booting the new kernel and reinstall catalyst drivers. There might be a command to recompile the kernel modules without reinstalling all of the drivers, but I dont know it.

OK that solved the problem, although it's strange... when I was upgrading to 2.26.28-15 I didn't need to reinstall the drivers. 

Thank you.

One more stupid question, 9.10 is coming soon and this will be my first ubuntu upgrade, Will my data in the /home will be deleted? 

/home is not on a diff partition, my ext4 mount point is only /

---

### Post by P4man on 2009-10-23
> **r5r4y said:**
> OK that solved the problem, although it's strange... when I was upgrading to 2.26.28-15 I didn't need to reinstall the drivers. 

Thank you.

One more stupid question, 9.10 is coming soon and this will be my first ubuntu upgrade, Will my data in the /home will be deleted? 

/home is not on a diff partition, my ext4 mount point is only /

If you do an upgrade from within ubuntu, using update-manager, then no, it wont be deleted. If you do an install from a livecd, then yes. Either way, its always a good idea to make a backup before doing a distribution upgrade.

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> If you do an upgrade from within ubuntu, using update-manager, then no, it wont be deleted. If you do an install from a livecd, then yes. Either way, its always a good idea to make a backup before doing a distribution upgrade.

It's a good idea to do a backup just because it's Friday.

---

