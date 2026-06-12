---
title: "VmwarePlayer broken after updates?"
date: 2006-06-17
forum: General Help
---

### Post by Pawel Stolowski on 2006-06-17
Hi,

VmwarePlayer from Ubuntu repo is broken after latest updates... The initscript for the player fails when loading modules... Or is it only for me?

---

### Post by jstueve on 2006-06-17
[http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)

---

### Post by Pawel Stolowski on 2006-06-17
The problem in that thread is different. They use genuine VmwarePlayer from vmware.com - this means they have to recompile kernel modules after kernel upgrades (with vmware-config.pl). I use vmware-player deb from Ubuntu repository. This package provides these modules but it looks like it needs to be updated to play with latest kernel. So - is anyone having this problem with up-to-date Dapper and vmware-player from Dapper repo?

---

### Post by Mirrorball on 2006-06-17
I loaded the modules myself.

```
sudo modprobe vmmon
```

---

### Post by Pawel Stolowski on 2006-06-17
It doesn't work... The module is missing.

cd /lib
yogin@pc:/lib$ uname -r
2.6.15-25-686
yogin@pc:/lib$ find ./ -name vmmon*
./modules/2.6.15-23-686/misc/vmmon.ko
./modules/2.6.15-23-386/misc/vmmon.ko
./modules/2.6.15-23-k7/misc/vmmon.ko

I think vmware-player needs to be updates in the repo.

---

### Post by jstueve on 2006-06-19
yeah, probably.. if the kernel updated, then the debs that depend on the kernel will slowly start to be updated.

---

