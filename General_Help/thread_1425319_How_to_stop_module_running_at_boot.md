---
title: "How to stop module running at boot"
date: 2010-03-08
forum: General Help
---

### Post by satimis on 2010-03-08
Hi folks,

Ubuntu 9.10 64bit
CPU - amd phenom II X4 955

I tried to stop kvm and kvm-amd modules to run at boot by adding;```

blacklist kvm
blacklist kvm-amd

```
at the end of /etc/modprobe.d/blacklist and reboot PC.

However it doesn't work.

$ ls /etc/modprobe.d/```

alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf        libpisock9.conf

```

Please advise which file I have to edit?  TIA

B.R.
satimis

---

