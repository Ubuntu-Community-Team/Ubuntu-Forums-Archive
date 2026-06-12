---
title: "boot hangs, but not every time"
date: 2009-12-27
forum: General Help
---

### Post by stoked acid city on 2009-12-27
i'm a semi-noob to linux, we've fooled around a bit but i never made a commitment before. now i've got an acer aspire one, dual booting unr 9.10 and xp, though i had this same issue with vanilla ubuntu (also 9.10). my netbook loads grub just fine, and grub boots windows just fine every time, but if i boot ubuntu, two out of three times it will go straight to a blinking cursor. it doesn't even make it to the ubuntu logo. the other 1/3 of the time it just works

what's up with that? it keeps getting worse. last night i tried twenty times without it booting. please help before this completely busts and i'm stuck for life with that bitch, windows xp!

---

### Post by stoked acid city on 2009-12-27
okay, after some troubleshooting this morning, i'm pretty positive it's a problem w/ agp. when i boot in recovery mode, if it hangs, it hangs right at the agpgart-intel part. i tried to blacklist it in modprobe.d, but it still loads at boot. how can I completely disable it?

---

### Post by stoked acid city on 2009-12-27
okay, I think it's somehow related to this bug - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694")

I added agpgart-intel, intel_agp, and "i915 modeset=1" via the workaround described in the second reply to that bug, and it booted six times and only hung once, so that's a good start

however, i've installed the rt kernel for low-latency audio, and grub won't boot into it at all (and never has). it still hangs around the AGP part of the boot, although it uses the generic linux drivers now instead of the intel ones.

could something else be causing problems too? i'm about to pull my hair out

---

### Post by stoked acid city on 2010-01-01
bump. any ideas at all? it's driving me crazy

---

