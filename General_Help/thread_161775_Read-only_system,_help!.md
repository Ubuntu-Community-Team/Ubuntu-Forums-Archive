---
title: "Read-only system, help!"
date: 2006-04-17
forum: General Help
---

### Post by meepy on 2006-04-17
Hello everyone.

Thanks for providing a good OS. But I ran into a few problems whilst updating the kernel to 2.6.16 following this HOWTO: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

Okay, everything went fine to start off with, I patched it, and started building the kernel. It was compiling for around 1-2 hours running a good speed, but suddenly a error popped up saying something with it could not access a file because the system was in read-only. I could from now on not start any other programs other those I had running. Only thing was to hit the switch which I did, in hope it would be solved on a reboot. But I was wrong.

During the reboot, GRUB loaded showing my old kernel, good luck I thought, but no, while it was booting the kernel it stopped at "Checking root filesystem (or something)" and a error came up saying my system was in a read-only mode, and that I should manually fix it with "mount -n -o remount, rw /" which I did. But it dident work, still the same error on reboot.

So basicly I'm stuck, I can not boot my system, not even in fail-safe mode whatsoever, it pops up with that read-only message during the reboot. Damnit.

I hope YOU know whats wrong, and how to save my system, thanks in advance! Peace out! :)

Regards, meep.

---

### Post by aysiu on 2006-04-17
Having never compiled a kernel myself, I don't know what went wrong, but maybe [this](http://ubuntuforums.org/showthread.php?t=24113) might help you boot into **a** kernel.

---

### Post by meepy on 2006-04-17
I can boot into the kernels but it stops when checking the system. And it comes with the "Check forced" and then it says my system is read-only.

---

