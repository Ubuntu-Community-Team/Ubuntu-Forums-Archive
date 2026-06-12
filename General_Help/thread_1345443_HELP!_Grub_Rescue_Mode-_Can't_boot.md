---
title: "HELP! Grub Rescue Mode- Can't boot"
date: 2009-12-04
forum: General Help
---

### Post by aaahmai on 2009-12-04
I am wondering whether anyone could help me.

I have received a netbook as present. Sony P688E. Has no DVD drive. Came with Windows Vista. It was so very slow so I decide to install Ubuntu. But it is still very slow. So I decide to use Windows Recovery Console to restore to original factory status so I can return it. 

NOW....... after i ran the Windows Recovery Console, the computer restart and can not boot!!

GRUB loading.
error: no such partition
grub rescue>

Could some one help me to resolve this? I need to at least be able to boot Windows otherwise I could not return the computer.

---

### Post by jbrown96 on 2009-12-04
Can you still boot the recovery partition? If so, then run ```
fixmbr
``` or maybe it's fixmbr.exe -- it's slipped my mind. That should replace grub with the windows loader.

---

### Post by aaahmai on 2009-12-04
I can not boot the recovery petition :(

Now when I start the computer. It takes me right in to Grub and I am paralyzed from there.

---

### Post by jbrown96 on 2009-12-04
The esiest way to fix this is really backwards. You need to reinstall Ubuntu, being careful not to overwrite your recovery partition. This will fix grub, and should give you an option to get to your recovery partition. Do the recovery to factory settings, then run fixmbr, and everything should work.

---

### Post by afrodeity on 2009-12-04
I usually do this with the RipLinux Recovery Disk, but I am told you can also do this with the Ubuntu CD. This will reinstall grub.

Boot up in recovery mode, drop to terminal

```
grub

find /boot/grub/stage1

root (hdx,x) <output of previous command = x >

setup (hd0)

quit

```

---

### Post by blondee.elizabeth on 2009-12-04
anyway, you should be running netbook remix or moblin on a netbook.  straight up ubuntu will not run as fast as the other two

---

### Post by jbrown96 on 2009-12-04
> **afrodeity said:**
> I usually do this with the RipLinux Recovery Disk, but I am told you can also do this with the Ubuntu CD. This will reinstall grub.

Boot up in recovery mode, drop to terminal

```
grub

find /boot/grub/stage1

root (hdx,x) <output of previous command = x >

setup (hd0)

quit

```

This does not work anymore. Ubuntu has switched to Grub2, which is substantially different than grub1. Please do not recommend this to people using 9.10 (fresh installs, not upgrades) because it will not work.

---

### Post by afrodeity on 2009-12-06
Oops, sorry. Forgot about Grub2.

---

### Post by Fargoneicon on 2009-12-06
so i am having the same problem loading 9.10 how do we get the grub2 to recover

---

