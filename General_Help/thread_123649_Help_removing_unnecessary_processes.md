---
title: "Help removing unnecessary processes?"
date: 2006-01-30
forum: General Help
---

### Post by z_diver on 2006-01-30
Is there a central database describing which processes do what on Ubuntu?  If I remember correctly, my default Breezy install booted 75 processes, did what I want and ran blindingly fast.  At this point, it still runs OK but starts ~90 processes at boot.  I'd love to tailor that a little and get closer 75.

Thanks,
Chuck

---

### Post by dcstar on 2006-01-30
[QUOTE=z_diver]Is there a central database describing which processes do what on Ubuntu?  If I remember correctly, my default Breezy install booted 75 processes, did what I want and ran blindingly fast.  At this point, it still runs OK but starts ~90 processes at boot.  I'd love to tailor that a little and get closer 75.

Thanks,
Chuck[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by z_diver on 2006-01-30
This is exactly what I was looking for.  Great Wiki material.
Thank you dcstar!

---

### Post by z_diver on 2006-01-31
For those of you that may be interested in knowing of a few likely candidates to turn off in /etc/rc2.d/ and /etc/rc6.d/ see if the below apply to you.

bluez-utils - Bluetooth
Raid
rsync
apmd - Advanced power management, redundant: acpid I left turned on
hotkey-setup - This is a desktop
hplip - HP printer and scanning software

---

