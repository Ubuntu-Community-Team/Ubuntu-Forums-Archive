---
title: "VMWare Player not working after update"
date: 2010-06-08
forum: General Help
---

### Post by gibxam on 2010-06-08
Hey everyone,

I'm running 10.04 and after an automatic update my vmware player is not working. When I try to run one of my windows vmachines (or any of them for that matter) the follow message pops up:
```

Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.
```
followed by:
```

Failed to initialize monitor device.
```
followed by:
```

The virtual machine is busy.

```

and then the screen just stays black and nothing happens. From reading past posts this looks like a problem that affected users a long time ago (like back in 7.10) but I couldn't find a solution. I already checked that my version is up to date and it is. Please help

---

### Post by gibxam on 2010-06-08
Problem solved! Found the solution here:
[http://forums.opensuse.org/get-help-here/applications/412745-vmware-error-after-reboot.html]("http://forums.opensuse.org/get-help-here/applications/412745-vmware-error-after-reboot.html")
bassically issue this command:
```

sudo vmware-modconfig --console --install-all

```

---

### Post by oomlout on 2010-08-27
Didn't work for me -- I don't even have a vmware-modconfig.  (VMware server 2.02)

---

### Post by astrotest on 2010-09-05
Have a look here:
[http://ubuntuforums.org/showthread.php?p=9725372](http://ubuntuforums.org/showthread.php?p=9725372)

---

### Post by dcstar on 2010-09-06
> **astrotest said:**
> Have a look here:
[http://ubuntuforums.org/showthread.php?p=9725372](http://ubuntuforums.org/showthread.php?p=9725372)

Amazing how the VM answers are in the VM forum, innit?

---

