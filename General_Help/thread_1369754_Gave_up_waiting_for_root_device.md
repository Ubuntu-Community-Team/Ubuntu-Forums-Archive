---
title: "Gave up waiting for root device"
date: 2010-01-01
forum: General Help
---

### Post by Kasracer on 2010-01-01
So I installed Ubuntu Netbook Remix 9.10 onto my Asus EeePC 1008HA netbook.

It worked perfectly and was pretty quick. Restarting, suspending and hibernating worked just fine but the very first time I shut it down, I can no longer boot back into Ubuntu.

I created 3 partitions.
/
/home
swap

All using the default filesystem (I'm still new but, I believe, it was EXT4?).

Anyway, now I only get this error stating "Gave up waiting for root device" when I attempt to boot.

I've tried typing in "exit" at the initramfs prompt as suggestions but it never works.

So I booted off of the USB stick I used to install and I took a look at my partitions. My boot partition now says "unknown" instead of the filesystem I used. So I used fsck on it which seemed to do something (it asked about future dates which it fixed). Then I attempted to use e2fsck but I always get the error "Invalid non-numeric argument to -P ("/dev/sda1")".

What can I do to attempt to resolve this? It's such a shame because everything worked perfectly and I had no problems with multiple restarts, hibernates and suspends but the first time I shut it down this starts happening. I didn't even hold the power button.

---

