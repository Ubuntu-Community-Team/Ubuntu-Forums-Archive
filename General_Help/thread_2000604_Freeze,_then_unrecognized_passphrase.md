---
title: "Freeze, then unrecognized passphrase"
date: 2012-06-09
forum: General Help
---

### Post by dangillmor on 2012-06-09
I've spent several days configuring a machine with Ubuntu and a bunch of stuff. I'm using an encrypted boot disk. There have been several hard freezes (memory tests show nothing wrong) and today's hard freeze has created a massive PITA. 

I powered it down (Thinkpad 220)  and started up again in recovery mode from the menu. But my passphrase is not recognized. After a number of attempts I was kicked into a shell with these messages:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls/dev)
ALERT!  /dev/mapper/ubuntu-root does not exist. Dropping to a shell!

I started up with a live-CD version of Ubuntu and tried unlocking the volume with the passphrase. Rejected with message, "Error unlocking device: cryptsetup exited with exit code 255: No key available with this passphrase."

Any ideas?

---

