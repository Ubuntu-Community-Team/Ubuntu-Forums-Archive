---
title: "One or more of the mounts listed in /etc/fstab cannot yet be mounted - a special case"
date: 2009-12-24
forum: General Help
---

### Post by Kyniker on 2009-12-24
Hi!

Yesterday I turned my notebook off, today I press the power button and my dear notebook gives me this wonderful x-mas gift:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for /dev/disk/by-uuid/<some-longe-alphnum-code>
Press ESC to enter a recovery shell

And here we hang. So I checked /dev/disk/by-uuid/ and - surprise!- my /home partition, sda12 wasn't in there. Suddenly. Overnight.
I changed the fstab entry for /home to /sda12 (instead of the uuid) /home, and now everything works fine.

But why the hell vanished the UUID for /home? How can I get it back?

Any advice welcome! Thanks.


------
Machine: hp EliteBook 6930p
OS: Kubuntu Karmic Koala (running stable for months now)
Yes, I did updates, but I can't remember if yesterday. Sorry.

---

### Post by Kyniker on 2009-12-24
Ironically right after writing the above post I rechecked /dev/disk/by-uuid and now there IS an entry for /dev/sda12. So I reverted my changes to /etc/fstab and rebooted _succsessfully_.
I don't mark this topic as solved, since I still don't know what actually went wrong.

---

