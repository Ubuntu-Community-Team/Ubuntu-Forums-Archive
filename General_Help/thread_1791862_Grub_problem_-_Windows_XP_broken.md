---
title: "Grub problem - Windows XP broken"
date: 2011-06-27
forum: General Help
---

### Post by kleinempfaenger on 2011-06-27
Hi,
I have a dual boot installed, with Ubuntu and Windows XP.
Last week I mounted the Windows partition in Ubuntu and since then I'm not able to start Windows. After the grub menu it shows the Windows XP boot screen, but after a while restarts.
Is there a way to recover the windows installation from Ubuntu, or another method without having to do a complete reinstall?
Thank you very much.
kl

---

### Post by ahears on 2011-06-27
Please look at this thread and see if it helps. 'http://ubuntuforums.org/showthread.php?t=1790574'. WBASAP.

---

### Post by seawolf167 on 2011-06-27
If Windows XP isn't booting properly, first try this:

Put your Windows XP cd in, boot off it, and select to enter the recovery console. Once there, type in the following command

```
fixboot C:\
```

Then restart and try to boot to Windows.

---

