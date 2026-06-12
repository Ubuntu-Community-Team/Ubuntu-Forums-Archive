---
title: "Hibernate isn't working (again?)"
date: 2009-12-03
forum: General Help
---

### Post by fowie on 2009-12-03
Karmic Koala on my Acer Timeline 3810T.  I started without a swap partition, but later made a 4GB swap, and the entry in my fstab is:
```

UUID=e92a6ca9-97c3-45ba-9ae2-f0988fe3aa2b none	swap sw,pri=1  0 0

```
swap seems to be mounted when I get into ubuntu, but I can't resume from hibernate.  /var/log/pm-suspend.log shows:

```

...
             total       used       free     shared    buffers     cached
Mem:       3961296    1742348    2218948          0     441156     717960
-/+ buffers/cache:     583232    3378064
Swap:      4192956          0    4192956
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55wicd hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Wed Dec  2 20:41:58 MST 2009: performing hibernate

```

and the computer does go into hibernate, but when I power back up, ubuntu starts up wanting to check my main hard disk (not the swap partition, but /dev/sda1 where ubuntu resides).  It finishes the check, reboots, and comes back up in a new boot, instead of restoring.  Am I missing something?

(If I skip disk checking, it still doesn't resume either)

---

