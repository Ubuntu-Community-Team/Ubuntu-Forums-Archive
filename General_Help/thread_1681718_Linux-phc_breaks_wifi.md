---
title: "Linux-phc breaks wifi"
date: 2011-02-04
forum: General Help
---

### Post by NoBugs! on 2011-02-04
The Linux-phc kernel, available [here]("https://launchpad.net/~linux-phc/+archive/ppa"), for 10.04, used to work fine for me, but starting awhile ago, it broke the wifi. I can't enable the broadcom driver, it says,

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

This log says:
....
....
2011-02-04 13:58:04,266 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 13:58:04,446 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 13:58:04,594 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 13:58:16,700 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 13:58:20,761 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-02-04 13:58:20,761 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-02-04 13:58:20,827 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 14:02:43,672 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 14:02:43,745 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 14:02:43,805 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 14:02:46,021 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2011-02-04 14:02:48,785 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-02-04 14:02:48,786 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-02-04 14:02:48,865 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

When booting the normal kernel, wifi works fine.

---

### Post by NoBugs! on 2011-02-06
I noticed when it is started up normally, the network connection info says the driver is "wl"... So is this a bug in wl or linux-phc??

---

### Post by NoBugs! on 2011-02-11
bump

---

