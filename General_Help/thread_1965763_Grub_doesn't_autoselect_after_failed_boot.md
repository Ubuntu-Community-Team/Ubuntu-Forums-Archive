---
title: "Grub doesn't autoselect after failed boot"
date: 2012-04-26
forum: General Help
---

### Post by P3t3r on 2012-04-26
I'm running a Ubuntu 12.04 (final beta) server machine which sometimes hangs at boot. This is ok, just going to the data center and powering it off/on again is no big deal.

What is not ok however, is that it doesn't automatically boot into the OS then. When nicely shut down, or shut down after boot (while OS is running), it automatically boots into Ubuntu, but when it hangs at boot, it displays the selection screen without making an automatic choice.

This is very annoying, since this causes me to go find a nearby keyboard, climb up to the 2m high rack where the machine is located, do all sorts of acrobatic moves to get the keyboard plugged in at the back, press enter and remove keyboard again.

Why is grub not configured by default to boot into the OS after X seconds, and how should I configure grub that even after an unsuccessful startup attempt it still just boots directly into Ubuntu?

---

### Post by P3t3r on 2012-04-28
Anyone? This should be a pretty common question no? Perhaps I should have placed it in the server-specific forum?

---

### Post by kiirokurisu on 2012-04-28
I have noticed this behaviour too, and while I'm not 100% sure, it seems like intended behaviour to me - e.g. if boot fails due to a kernel update, it stops at the menu screen to let you choose an older kernel.

---

### Post by P3t3r on 2012-04-28
> **kiirokurisu said:**
> I have noticed this behaviour too, and while I'm not 100% sure, it seems like intended behaviour to me - e.g. if boot fails due to a kernel update, it stops at the menu screen to let you choose an older kernel.

But there is only 1 kernel (as I didn't install any updates). And I also expected it to be "intended" behaviour, but I want to know how to *change* this behaviour. Either by completely turning it off (auto booting the last kernel no matter what), or by having a timer as usual (autobooting the last kernel if no other action is taken for 30 seconds) or by going to this screen only after 3/4/5 subsequent failed boots. Anything works, as long I don't need a keyboard plugged into every time this happens...

---

### Post by Monotoko on 2012-04-28
Well, why does it hang? That's probably the easiest place to start. Have you got the latest kernel?

---

### Post by P3t3r on 2012-04-28
> **Monotoko said:**
> Well, why does it hang? That's probably the easiest place to start. Have you got the latest kernel?It hangs because the previous boot was incomplete. So it lets me select other options such as memcheck. But it has no timer or so, which means that without a keyboard I can't boot into the machine anymore.

---

### Post by Monotoko on 2012-04-28
You're missing my point, I mean why does the previous boot fail to cause it to then be powered off/on again?

---

### Post by P3t3r on 2012-04-28
> **Monotoko said:**
> You're missing my point, I mean why does the previous boot fail to cause it to then be powered off/on again?
I don't know. It happens. It's an experimental setup with 8 GPUs, and I can well imagine that the kernel designers didn't take this possibility in mind (regarding certain time-outs probably). And I don't blame them, it's not common for a user to have 8 high-end GPUs and nevertheless it boots up correctly 80% of the time. 

So therefor, it seems more within reach to resolve the grub problem, than to dig through the entire kernel to find all relevant time-outs that should be adapted for the few souls like me that want 8 GPUs on their system. ;)

---

### Post by Monotoko on 2012-04-28
Ahhh fair enough! I haven't really caught up on grub2 configuration and I'm on Windows at the moment, but there may be something in /etc/default/grub that you can change.

Update: After a bit of digging, you want to take the "recordfail" variable out of the equation.

Editing this file could work for you from another thread (5th post down):
/etc/grub.d/10_linux

[http://ubuntuforums.org/archive/index.php/t-1282539.html](http://ubuntuforums.org/archive/index.php/t-1282539.html)

---

