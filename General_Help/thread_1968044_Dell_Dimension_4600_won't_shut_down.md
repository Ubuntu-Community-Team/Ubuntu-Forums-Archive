---
title: "Dell Dimension 4600 won't shut down"
date: 2012-04-28
forum: General Help
---

### Post by raddoc on 2012-04-28
Having run Ubuntu 7.10 happily on this machine for years, I updraded to 11.10 and then 12.04. After the upgrade it restarts itself after shut down all the time. The only way to shut down is to reload 7.10 from the Grub menu and to shut down out of 7.10.
Shutting down from Terminal makes no difference.
Has anyone got any suggestions?

---

### Post by dorktaped on 2012-04-28
I don't think that you and I are having the exact same problem but my Dell Latitude D830 is having shut down issues as well. It hangs on a black screen when I attempt to shut it down and I have to hold the power button for it to actually power all the way down.

I've just got to say, this is my third upgrade and I've never had so many problems afterwards. I'm thinking about just wiping the partition and doing a fresh install of 12.04 to see if that will solve it.

---

### Post by raddoc on 2012-04-29
I feel it may be a hardware issue rather than an operating system one. I wonder if it has anything to do with automatic restarting after accidental power outage. The BIOS might provide for this but I cannot see how to disable it, if it does.

---

### Post by CharlesA on 2012-04-29
I had a similar thing happen on my new i7 box - it would reboot instead of shutdown when the shutdown command was run.

BIOS update fixed it.

Have you checked to see if there is a BIOS update for that machine?

> **dorktaped said:**
> I don't think that you and I are having the exact same problem but my Dell Latitude D830 is having shut down issues as well. It hangs on a black screen when I attempt to shut it down and I have to hold the power button for it to actually power all the way down.

I've just got to say, this is my third upgrade and I've never had so many problems afterwards. I'm thinking about just wiping the partition and doing a fresh install of 12.04 to see if that will solve it.

This sounds like a similar problem to what I am having now with 12.04 - if you run "sudo poweroff" does it shutdown?

---

