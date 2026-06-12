---
title: "which kernel version is installed with 11.10"
date: 2011-10-22
forum: General Help
---

### Post by utnubuuser on 2011-10-22
Hello,

Anyone know off-hand which kernel version, (full number for booting from grub-rescue prompt ie: shown in grub-menu list at boot), is installed when installing from 11.10 liveCD?

Thanks

---

### Post by masgeeks on 2011-10-22
3.0.0-12 I believe...

---

### Post by deloquencia on 2011-10-22
It's 3.0. 3.1 didn't made it into 11.10 (see [https://lists.ubuntu.com/archives/kernel-team/2011-September/016964.html](https://lists.ubuntu.com/archives/kernel-team/2011-September/016964.html)).
If in doubt run **uname -r** in a terminal

---

### Post by utnubuuser on 2011-10-22
I don't have it installed - i'm running lucid...  I'm asking on behalf of someone who's trying to boot from rescue-prompt, in which case uname-r doesn't do you any good...

in this [http://ubuntuforums.org/showthread.php?t=1866885]("http://ubuntuforums.org/showthread.php?t=1866885") thread

maybe someone could re-boot and check the grub-menu list? Thanks

---

### Post by DanR01 on 2011-10-22
Try:

```

```uname -r```

```

---

### Post by utnubuuser on 2011-10-22
danR01.... you should read the posts before responding...  thanks anyway...

---

### Post by drawkcab on 2011-10-22
> **masgeeks said:**
> 3.0.0-12 I believe...

This is what I'm running.

---

### Post by utnubuuser on 2011-10-22
and is this the kernel that's installed when you first install 11.10, or is this an updated, post install kernel?

I was specifically looking for the kernel that is installed during the install process, and often, after installation, when the most current updates are downloaded, one of the first things that gets updated is the kernel.  Hence my suggestion to re-boot and check the grub-menu list...

thanks

---

### Post by utnubuuser on 2011-10-22
and is this the kernel that's installed when you first install 11.10, or is this an updated, post install kernel?

I was specifically looking for the kernel that is installed during the install process, and often, after installation, when the most current updates are downloaded, one of the first things that gets updated is the kernel.  Hence my suggestion to re-boot and check the grub-menu list...

thanks

---

### Post by deloquencia on 2011-10-22
To make things more clear I checked now also the Release Notes at [https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Linux_3.0_Kernel](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Linux_3.0_Kernel) - it's 3.0 - 3.0.4 to be exact.

"Ubuntu 11.10 includes the 3.0.0-12.20 Ubuntu kernel which brings the 3.0 upstream kernel, the latest mainline release. The Ubuntu kernel is based on the linux v3.0.4 upstream stable kernel."

So it's the default kernel which is installed in first hand, when you install 11.10 for the first time.

---

