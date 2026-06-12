---
title: "Lucid freezes workaround query"
date: 2010-10-08
forum: General Help
---

### Post by rdh61 on 2010-10-08
Hi,
I have the issue described in

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Workaround A allows me to boot, but to make changes permanent, the above suggests I run the following command:

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf[FONT=monospace]
[/FONT]sudo update-initramfs -u[FONT=monospace]

[/FONT]But when I do this I am told that the 'u' parameter does not exist in tee. There are only 'a' or 'i' parameters.

Can anyone shed any light on this?

Thanks.

---

### Post by Rmantingh on 2010-10-08
It seems to me that the 2 command lines got mixed up somehow. It looks like the "-u" of the second line is being used by the tee command on the first line. Try copying each individual line into a terminal and execute them separately and see if that works better.

---

### Post by rdh61 on 2010-10-09
Yes, that makes sense.

In fact I don't need this any more. I simply wrote my changes ("quiet i915.modeset=1" instead of "quiet splash") into /etc/default/grub and that seems to have done the trick.

Many thanks anyway.

---

