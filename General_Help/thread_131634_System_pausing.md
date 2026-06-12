---
title: "System pausing"
date: 2006-02-16
forum: General Help
---

### Post by blx_286 on 2006-02-16
I am having a problem with my laptop and I hope someone can help. I have a Dell Inspiron 4000 with a USB hub running a wireless mouse, flash drive and Netgear WG111. It seems like my laptop pauses for about 5 - 10 seconds every minute or two. I know that's kind of vague, but I'm not sure what info is needed to point me in the right direction.

Thanks,
Tim

---

### Post by blx_286 on 2006-02-16
I think I may have found my pausing problem. I found this when I typed dmesg -

[4294909.352000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294909.352000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294909.425000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294909.425000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294919.322000] cpufreq: change failed with new_state 0 and result 0
[4294921.250000] cpufreq: change failed with new_state 1 and result 0
[4294995.401000] cpufreq: change failed with new_state 0 and result 0
[4294999.744000] cpufreq: change failed with new_state 1 and result 0
[4295047.174000] cpufreq: change failed with new_state 0 and result 0
[4295050.341000] cpufreq: change failed with new_state 1 and result 0
[4295068.486000] cpufreq: change failed with new_state 0 and result 0
[4295071.821000] cpufreq: change failed with new_state 1 and result 0
[4295093.079000] cpufreq: change failed with new_state 0 and result 0
[4295095.035000] cpufreq: change failed with new_state 1 and result 0
[4295118.312000] cpufreq: change failed with new_state 0 and result 0
[4295122.462000] cpufreq: change failed with new_state 1 and result 0
[4295129.474000] cpufreq: change failed with new_state 0 and result 0

There was alot more of the cpufreq stuff, but you get the idea. I found a thread about both of these and fixed them. Seems to be running better, so I guess one of those was causing the problem.

Thanks,
Tim

---

