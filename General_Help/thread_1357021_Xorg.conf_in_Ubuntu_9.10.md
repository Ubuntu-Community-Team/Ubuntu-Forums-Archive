---
title: "Xorg.conf in Ubuntu 9.10"
date: 2009-12-16
forum: General Help
---

### Post by federico.bond on 2009-12-16
Hi,
I installed Ubuntu in a computer and the screen borders were off by some pixels in the LG Flatron L1900R monitor.

I ran xvidtune and managed to align it perfectly. I copied the ModeLine it gave me and searched for the Xorg.conf file.

As I could not find it I ran "sudo Xorg -configure" and copied the new xorg.conf file to /etc/X11/ and added the ModeLine to it.

Upon restarting X I found out that it didn't take into account the new setting.

Did I miss something or did something wrong?

Thanks,

---

