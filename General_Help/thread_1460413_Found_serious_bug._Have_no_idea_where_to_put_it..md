---
title: "Found serious bug. Have no idea where to put it."
date: 2010-04-22
forum: General Help
---

### Post by vrbik on 2010-04-22
I have a new Lenovo (thinkpad) x100e laptop.

I've recently installed the new Ubuntu 10.02 distro and have found the oddest bug.

If my power cord is disconnected (i.e. if i'm running off battery power) then the login window locks up. 

Conversely, if the power cord _is_ connected then things work as usually.

(Also, trying to adjust brightness causes a crash --- but I suspect that this is not odd).

Could someone please direct me to where I should put this information.

---

### Post by Chronon on 2010-04-22
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

However, this bug seems to have been reported already: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535653)

---

### Post by vrbik on 2010-04-22
Thanks!

(I did read through all the bug reporting docs before this and still came out unsure)

And yes; this is precisely the same problem.

---

### Post by Chronon on 2010-04-22
It looks like there is a workaround or two that could work until the bug is fixed properly.  It looks like someone was saying the crash could be avoided by disabling ACPI.

---

### Post by Coucouf on 2010-05-01
This is a known problem with AMD RS780 chipset (Radeon HD3200) and kernel modesetting (KMS), which is enabled by default in Lucid.

To disable KMS, you should do the following in a terminal:
1. Modify GRUB configuration
```
sudo nano /etc/default/grub
```
Change line 10 from:
```
GRUB_CMDLINE_LINUX=""
```
to:
```
GRUB_CMDLINE_LINUX="radeon.modeset=0"
```
and save with Ctrl+X, O, Enter.

2. Run the GRUB configuration update utility:
```
sudo update-grub
```

This should get you going. You loose high-res boot splash, but win a working laptop. :)

---

