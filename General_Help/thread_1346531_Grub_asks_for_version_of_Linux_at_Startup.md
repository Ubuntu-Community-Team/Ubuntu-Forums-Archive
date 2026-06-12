---
title: "Grub asks for version of Linux at Startup"
date: 2009-12-05
forum: General Help
---

### Post by The Pinny Parlour on 2009-12-05
Hi

After a recent update, my GRUB says the following at startup and I would like to know why and how to not have it show and just auto boot into Ubuntu.

```
GNU Grub Version 1.97~beta4
Ubuntu, Linux 2.6.31.15 generic
Ubuntu, Linux 2.6.31.15 generic (recovery mode)
Ubuntu, Linux 2.6.31.14 generic
Ubuntu, Linux 2.6.31.14 generic (recovery mode)
Memory Test

```

Thanks in advance

---

### Post by Shazaam on 2009-12-05
StartupManager (get it through Synaptic) will offer a basic gui way to tweak the default kernel choice and timeout value. At the moment the Karmic version doesn't have all of the options that earlier versions of Ubuntu had. From what I have read the devs are hard at work getting it better for grub2.
Otherwise you can find posts here on the forums dealing with how to manually edit grub2. Follow them VERY carefully as a mistake can cause problems.

---

### Post by Bigneil on 2009-12-05
i'm with the startup manager camp.  just install it and you can easily set your startup the the way you would like it without risk.

---

### Post by The Pinny Parlour on 2009-12-05
Plugged in a PS2 keyboard and choose which one I wanted, and that seems to set it in stone.  All good now.  :)

---

### Post by audiomick on 2009-12-05
Hallo.

Because no-one explained: The reason you suddenly had several entries is because updates don't chuck out the old kernels.

In Grub at least, presumably in grub2 also, there is an option for how long it will wait for you to choose, or if it will wait at all.

To get around having to drag out the old keyboard for installations etc., I enabled various USB options in BIOS. This means my USB keyboard and mouse are recognized well before even GRUB starts, let alone the Linux boot up.

---

### Post by Leppie on 2009-12-05
You can actually set GRUB to hide, and the timeout to boot into the default system. Have a read through [the grub2 guide]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+guide")

You can also modify the entries scripts.

---

### Post by audiomick on 2009-12-05
This tutorial looks good too:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

