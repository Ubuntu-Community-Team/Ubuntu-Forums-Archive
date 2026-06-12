---
title: "To many listings."
date: 2010-07-16
forum: General Help
---

### Post by waltwin on 2010-07-16
I have Windows 7 and ubuntu 9.04 on the same drive. When my system boots up I get a screen with a listing of 9 variations of Windows and ubuntu 9.04 from which to select. I only want one of each.

How can I delete the ones I don't want?

Thank you for any help.

waltwin

---

### Post by ST3ALTHPSYCH0 on 2010-07-16
Check which Linux kernel you're booting into. Go into Synaptic and completely remove the rest. Open a terminal :
```

sudo update-grub

```

Reboot.

---

### Post by Mark Phelps on 2010-07-17
> **waltwin said:**
> I have Windows 7 and ubuntu 9.04 on the same drive. When my system boots up I get a screen with a listing of 9 variations of Windows and ubuntu 9.04 from which to select. I only want one of each.

How can I delete the ones I don't want?

Thank you for any help.

waltwin

Be careful you don't delete the ones you NEED ...

It's a good idea to keep two Ubuntu kernel versions in the boot menu, after upgrading the kernel.  That way, if you have problems using the new kernel, you can boot back into the old kernel.

As to Win7, all to often, GRUB2 creates two entries -- because it sees bootmgr on one partition and winload.exe on the other partition. Fortunately, you can't delete those entries easily.  So, I would leave them alone.

---

### Post by waltwin on 2010-07-17
> **ST3ALTHPSYCH0 said:**
> Check which Linux kernel you're booting into. Go into Synaptic and completely remove the rest. Open a terminal :
```

sudo update-grub

```

Reboot.
Thank you for the response. I don't know how to check which Linux kernel I am booting into. I went  into Synaptic but I am not sure where to go to delete the items I do not want. Sorry to let my ignorance show but as you can tell I really need guidance!

---

### Post by lidex on 2010-07-18
The easiest way to manage your kernels is to use ubuntu-tweak:
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

As *Mr. Phelps* points out, always retain an older kernel for backup!!

Find your current kernel version:
In a Terminal="Applications->Accessories->Terminal"
```
uname -a
```

---

### Post by ST3ALTHPSYCH0 on 2010-07-18
The kernel versions are the numbers in that Grub list, and the newest is always on top. I always just write down the numbers of the kernel I don't want. Search for those numbers in Synaptic. You'll see entries that say something to the effect of "Linux_headers_***_ver#" right click and mark for complete removal.
Someone who knows the system a little better may have a more efficient way. I only dabble in Linux, and can't ever remember which directory the kernels are stored in or anything.

---

