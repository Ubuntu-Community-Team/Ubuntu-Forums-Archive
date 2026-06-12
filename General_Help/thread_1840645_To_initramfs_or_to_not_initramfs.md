---
title: "To initramfs or to not initramfs"
date: 2011-09-07
forum: General Help
---

### Post by towheedm on 2011-09-07
Over the last 4 months or so, I have been on a quest to make my clunky old 8-9 old machine run as smooth as it did with Karmic.  This quest has taken me on several different paths: from patching and building custom kernels to patching and building my nvidia drivers from source.

I started of learning as much as I could on building mainline kernel, starting from 2.6.39.1 to 3.0.0.1.  I eventually settled on 2.6.39.3, patched with apparmor 2.4, the BFS cpu scheduler and the BFQ io scheduler.  After a very steep learning curve, I now have what I hope is my final kernel build with all of my modules (only the ones I need of course) statically linked.

My next step was to improve the performance of my video sub-system.  With a very old GeForce FX5200 (128MB RAM), my desktop was not as snappy as I thought it should be.  So after activating the overclocking settings and patching the source to enable AGP Fast Writes by default, my desktop is now so much more responsive, with full screen flash and a kernel build running together without much degradation to the full screen video.

I have built my kernel without support for any initial ram filesystem.  Without an initramfs having to load, my time from boot to gdm have dropped from 32 sec (with Ubuntu stock kernel) to 16 second with my custom kernel.  A huge decrease in time.

With all that said, my question is simply this:
Is there any disadvantage of not using an initramfs over using one?

Now I understand that initramfs also runs cetain scripts during bootup.  I am yet to look at those to see what they do.  Is there something I might be overlooking?

Any thoughts on this would be truly appreciated.

Thanks.

---

### Post by towheedm on 2011-09-08
Seriously, no one one this forum has any suggestions on this?

---

### Post by sandyd on 2011-09-08
The initramfs just manages stuff such as netbooting, mdadm, .etc .etc.

If you have a standard setup, you shouldn't need initramfs.

p.s.
If your curious on what the initramfs in ubuntu does, I gunziped, and cpioed the initramfs back to its original form. You can see the script that is run when loading the initramfs here -> [http://pastebin.com/LcYMDSyK](http://pastebin.com/LcYMDSyK)

---

### Post by towheedm on 2011-09-08
Thanks for the script.  Yes, I understand that the initramfs loads for the very least, all of the drivers needed to mount the root filesystem.  I guess then there is no real disadvantage to not using an initramfs once I have all of my necessary drivers statically linked.

The only situation I've seen so far, is that I do not get to the console automatically if I boot into init 1 mode or even to init 3 without any video drivers installed.  I always have to switch to the console with Ctrl-Alt-Fx.  I just I may be able to this from my init scripts.  Will have to look into that more as I'm not too familiar with how these scripts load: Kxx, Sxx etc.

---

