---
title: "ubuntu on external drive - grub query"
date: 2010-01-25
forum: General Help
---

### Post by rdh61 on 2010-01-25
Hi,
I have installed Ubuntu 9.10 on an external drive, leaving my onboard HD for WinXP.
I had counted on being able to boot into WinXP even when without the external drive.
But if I attempt that grub says disc not encountered (or words to that effect), leaving me no boot options at all.
So, my question is:
Is there a way of installing Ubuntu onto an external drive but still being able to access the onboard HD (for WinXP) in the absence of the external drive?
Thanks.

---

### Post by scouser73 on 2010-01-25
Have a look at the Ubuntu documentation, [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by rdh61 on 2010-02-01
Thanks, the link was useful. The solution was of course to have grub on the external disc and to fix the mbr of my onboard HD. This allows me to use Ubuntu by booting into the external drive from the bios boot options. Otherwise the computer will normally boot into Windows, just as I wanted.

---

