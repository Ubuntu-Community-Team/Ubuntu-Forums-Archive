---
title: "No longer boots after system hang"
date: 2012-06-22
forum: General Help
---

### Post by Hovercat on 2012-06-22
Recently, my system has been hanging after about 2-3 days, and I couldn't figure out why. From what I figured out upon my research, it was something involving rsyslog and my kernel (2.6.32.41-generic), so I upgraded to 2.6.32.41-server, which is the the same kernel my other Ubuntu system runs without an issue. I went to check my server earlier and it was down again, and I noticed that the CPU fan was spinning at less than 1000RPM, so I decided to use a 4-pin to 3-pin adapter to run the fan at a full 12v. Upon rebooting, after GRUB loaded, the screen would remain blank with no HDD activity. I rebooted and attempted recovery mode, but it freezes a after

```
console (tty0) enabled
```

What can I do? I'm running Ubuntu 10.04.4 x64.

**Edit**: Solved, turns out a stick of RAM went bad. Memtest86+ spewed out errors. Replaced the stick and it boots up fine.

---

