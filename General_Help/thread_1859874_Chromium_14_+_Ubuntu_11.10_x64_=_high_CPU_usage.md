---
title: "Chromium 14 + Ubuntu 11.10 x64 = high CPU usage"
date: 2011-10-14
forum: General Help
---

### Post by acambre on 2011-10-14
I have two Ubuntu 11.10 x64 VMs: one I upgraded from 11.04 and another that I installed from an ISO.

I am running the latest (as of now) stable release of Chromium 14.

Chromium is generally slow, but when I have any extensions enabled, it crawls and sucks down CPU until I disable the plugins. The problem does not appear to be correlated to any plugin; just having *any* plugins enabled appears to contribute to this.

This problem never happened on Ubuntu 11.04.

Anyone else getting this?

---

### Post by acambre on 2011-10-14
Just did a new 32 bit install of 11.10. Cannot reproduce this problem.

---

### Post by collisionystm on 2011-10-14
> **acambre said:**
> I have two Ubuntu 11.10 x64 VMs: one I upgraded from 11.04 and another that I installed from an ISO.

I am running the latest (as of now) stable release of Chromium 14.

Chromium is generally slow, but when I have any extensions enabled, it crawls and sucks down CPU until I disable the plugins. The problem does not appear to be correlated to any plugin; just having *any* plugins enabled appears to contribute to this.

This problem never happened on Ubuntu 11.04.

Anyone else getting this?

Chromium and chrome are having problems with unity.

if you want to use it, run gnome-shell

---

### Post by acambre on 2011-10-14
> **collisionystm said:**
> Chromium and chrome are having problems with unity.

if you want to use it, run gnome-shell
I still wonder why I didn't get this with 11.04?

---

### Post by Nirro on 2011-10-14
I have the same problem with Chrome = VERY SLOW now after upgrading to 11.10
What's going on with the release ?

---

### Post by collisionystm on 2011-10-14
> **acambre said:**
> I still wonder why I didn't get this with 11.04?

11.10 is running 'unity' but the guts have been ripped out and replaced.

Its a new Frankenstein that needs a little T.L.C.

---

### Post by grazer on 2011-11-15
> **collisionystm said:**
> 11.10 is running 'unity' but the guts have been ripped out and replaced.

Its a new Frankenstein that needs a little T.L.C.

Do you have specific issues you could link to?

I'm finding that /usr/bin/X CPU usage goes through the roof (90+%) and the system becomes lagging.  It happens when I'm running a bunch of Chrome windows - see [Ask Ubuntu 78237]("http://askubuntu.com/questions/78237/unity-3d-with-nvidia-driver-becomes-very-slow-and-laggy")

---

