---
title: "Compcache 64-bit Bug"
date: 2010-10-29
forum: General Help
---

### Post by NightwishFan on 2010-10-29
The Ubuntu method to enable compcache is to open /etc/initramfs-tools/initramfs.conf and set a positive value to compcache. This does not work for me in 64-bit it does not enable it, but does create the ramzswap0. When I try to swapon the ramzswap it gives me this error:

```
sudo swapon /dev/ramzswap0
swapon: /dev/ramzswap0: read swap header failed: Invalid argument

```

I have a friend that confirmed it does work on 32-bit.

I am using 64-bit Maverick if that helps.

EDIT: Update, I find running "sudo /usr/lib/initramfs-tools/bin/rzscontrol /dev/ramzswap0 --init && sudo swapon -p 100 /dev/ramzswap0" works, though I have to do this on every reboot, which seems to be what the initramfs should already do on it's own.

---

### Post by Helkaluin on 2010-11-03
I can confirm this, also on Maverick x64. Perhaps file a bug?

I'm looking into the stuff in /usr/share/initramfs-tools/hooks/ now, yet I'm but a mere user and not a hacker here...

---

### Post by NightwishFan on 2010-11-03
I just added the one command to rc.local. A bug was filed here: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317)

I do not think the issue is the same though. I will try compcache on 10.04.

---

### Post by NightwishFan on 2010-11-03
Update: It works out of the box on lucid 64-bit. :/ I will try to get a diff of some related packages.

---

### Post by blasted001 on 2011-01-24
Well I'm not sure what your friend did, but this is not a 64-bit specific bug. I tested it on 3 laptops of different brands and compcache is broken on all of them (exhibiting the behavior you described.) Think I'll start another thread to emphasize the scope of the issue. Where's the appropriate place to report this bug?

---

