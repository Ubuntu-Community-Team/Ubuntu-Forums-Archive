---
title: "Hardware error and mcelog"
date: 2011-06-29
forum: General Help
---

### Post by TheCat on 2011-06-29
My computer regularly crashes if left running for 20 or more minutes without user interaction.  In attempting to diagnose the problem, I've disabled the screensaver and power management with no success, so I'm pretty sure it's not either of those.

Now I'm digging into the logs and I find this in kern.log:

```
Jun 29 06:31:14 machinename kernel: [ 1200.000032] [Hardware Error]: No human readable MCE decoding support on this CPU type.
Jun 29 06:31:14 machinename kernel: [ 1200.000038] [Hardware Error]: Run the message through 'mcelog --ascii' to decode.
Jun 29 06:31:14 machinename kernel: [ 1200.000042] [Hardware Error]: Machine check events logged
```

Any suggestions for where to look next would be welcome.  The few things I've found about mcelog haven't helped.

---

### Post by dino99 on 2011-06-29
a few things to check:
- free partition(s) space
- are fans working ?
- hardware not too dusty ?

should force a fsck on next boot: sudo shutdown -r now

[https://secure.wikimedia.org/wikipedia/en/wiki/Machine_Check_Exception](https://secure.wikimedia.org/wikipedia/en/wiki/Machine_Check_Exception)

---

### Post by TheCat on 2011-06-29
Thanks for the tips.

What I'd really like to know is what piece of hardware is causing the error.  Is there any way to read the actual error log and find out?

---

