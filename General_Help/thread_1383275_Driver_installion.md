---
title: "Driver installion"
date: 2010-01-17
forum: General Help
---

### Post by Jackzor on 2010-01-17
I want to install this ```
NVIDIA-Linux-x86-190.53-pkg1.run
```

But.. I dunno how.. Someone walk me through this?

Its a driver.....btw...

---

### Post by Crafty Kisses on 2010-01-17
It should be fairly simple, you have to stop GDM first, then run the package, so you can run:
```
/etc/init.d/gdm stop
cd Desktop
sudo sh ./NVIDIA-Linux-x86-190.53-pkg1
```
That is if you have the nVidia driver saved to your desktop, so if you have the driver saved somewhere else, the command would obviously be different.

---

### Post by Jackzor on 2010-01-17
> **Crafty Kisses said:**
> It should be fairly simple, you have to stop GDM first, then run the package, so you can run:
```
/etc/init.d/gdm stop
cd Desktop
sudo sh ./NVIDIA-Linux-x86-190.53-pkg1
```
That is if you have the nVidia driver saved to your desktop, so if you have the driver saved somewhere else, the command would obviously be different.

```
nicholas@nicholas-laptop:~$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.78" (uid=1000 pid=11243 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```

Um... I can't figure this out lol.

---

### Post by 3rdalbum on 2010-01-17
> **Jackzor said:**
> ```
nicholas@nicholas-laptop:~$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.78" (uid=1000 pid=11243 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```

Um... I can't figure this out lol.

You need to get out of the Windows mindset with this.

The 185 driver is available from the Hardware Drivers program in Ubuntu. If you don't see it, then either your Nvidia card is a little too new or you need to Reload your package list.

If your card is so new that it requires the 190 driver, or you do absolutely need this new driver for some reason, there is a PPA (Personal Package Archive repository) containing the driver. Follow this link:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

After adding the PPA, you can install the "nvidia-graphics-drivers-190" package, or even the "nvidia-graphics-drivers-195" package if you like living on the bleeding edge.

The advantages of this are:

1. Your system will keep the Nvidia driver up-to-date
2. You won't need to keep reinstalling the driver every time there's a kernel update
3. It's much easier to install, and you don't need to turn off X to install it.

---

