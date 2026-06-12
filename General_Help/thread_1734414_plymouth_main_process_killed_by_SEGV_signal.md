---
title: "plymouth main process killed by SEGV signal"
date: 2011-04-20
forum: General Help
---

### Post by torne on 2011-04-20
I just installed Ubuntu on a Cr-48 netbook, which has an odd custom bios which can't boot regular bootloaders/kernels. I'm therefore using the existing kernel on the machine rather than the Ubuntu one, with no initrd/initramfs, just booting directly to the Ubuntu root filesystem. It's just a minimal text mode install right now, from the alternate installer.

At boot time, plymouth crashes. It doesn't seem to actually affect the system, everything still boots just fine, but it doesn't seem like it should be doing that ;)

I get:

```

mountall: Disconnected from Plymouth
init: plymouth main process (70) killed by SEGV signal
init: plymouth-splash main process (190) terminated with status 2
init: plymouth-log main process (393) terminated with status 1

```

mountall is still successfully mounting all the filesystems so presumably it's just complaining that plymouth died while it was trying to talk to it...

Any ideas what's causing this? I don't particularly care whether plymouth actually puts up a splash screen or not, but having it crash is unnerving :)

---

### Post by rajivecn on 2011-06-21
> **torne said:**
> I just installed Ubuntu on a Cr-48 netbook, which has an odd custom bios which can't boot regular bootloaders/kernels. I'm therefore using the existing kernel on the machine rather than the Ubuntu one, with no initrd/initramfs, just booting directly to the Ubuntu root filesystem. It's just a minimal text mode install right now, from the alternate installer.

At boot time, plymouth crashes. It doesn't seem to actually affect the system, everything still boots just fine, but it doesn't seem like it should be doing that ;)

I get:

```

mountall: Disconnected from Plymouth
init: plymouth main process (70) killed by SEGV signal
init: plymouth-splash main process (190) terminated with status 2
init: plymouth-log main process (393) terminated with status 1

```

mountall is still successfully mounting all the filesystems so presumably it's just complaining that plymouth died while it was trying to talk to it...

Any ideas what's causing this? I don't particularly care whether plymouth actually puts up a splash screen or not, but having it crash is unnerving :)

Check this link;
[http://jonmccune.wordpress.com/2010/07/27/plymouth-main-process-341-killed-by-segv-signal/](http://jonmccune.wordpress.com/2010/07/27/plymouth-main-process-341-killed-by-segv-signal/)

---

### Post by linas on 2012-05-07
Its happening after upgrade to precise pangolin.  But then it happened on Oneiric as well.  I'm disappointed that it didn't "fix itself", after the upgrade.  The boot sequence is borked for me, I have to do the last few bits manually.  (Luckily I boot only one or twice a year, cause wow, is it ever painful...)

---

