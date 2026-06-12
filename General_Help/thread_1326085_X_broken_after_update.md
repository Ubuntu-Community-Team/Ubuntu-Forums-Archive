---
title: "X broken after update"
date: 2009-11-14
forum: General Help
---

### Post by Pro-reason on 2009-11-14
I recently did an update, which included a kernel update, and now Ubuntu will not start up cleanly.  I get the ‘low-graphics mode’ warning.  I find that if I choose to fall back to a terminal, the log-in screen will appear within a few seconds (whether I log into the terminal or not), and then I am able to use the system normally, with Compiz working etc.

What tweaks do I need to make to /etc/X11/xorg.conf to fix this?

```
$ uname -a
Linux chameleon 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
```

---

### Post by paulsmith99 on 2009-11-18
I got exactly this today. My Mythbuntu box usually runs for days/months without a reboot so that's probably why I've only just noticed because of a recent reboot.

I have got round it temporarily but choosing the previous kernel in grub. In my case it is 2.6.31-14-generic. I'm back working fully - sorry I can't offer any reason. At least I'm not the only one to encounter this headache.

---

### Post by Confuzius on 2009-11-18
Are you running a video driver not from a repository?
Sounds like you need to rebuild the kernel module for your driver since it no longer matches the kernel.

---

### Post by Pro-reason on 2009-11-18
> **paulsmith99 said:**
> I got exactly this today. My Mythbuntu box usually runs for days/months without a reboot so that's probably why I've only just noticed because of a recent reboot.

I have got round it temporarily but choosing the previous kernel in grub. In my case it is 2.6.31-14-generic. I'm back working fully - sorry I can't offer any reason. At least I'm not the only one to encounter this headache.
I tried different kernels, to no avail.  Sometimes it made it impossible to get X running at all.  Perhaps on those occasions reinstalling the Nvidia drivers would have helped.

I use both GNOME and KDE.  I have now removed KDM (forcing GDM to be used instead).  This has magically resolved the issue.  Bizarre.

> **Confuzius said:**
> Are you running a video driver not from a repository?
Sounds like you need to rebuild the kernel module for your driver since it no longer matches the kernel.

If the driver module were not there, how would we be able to eventually start X and use Compiz?

---

