---
title: "Is there a way to find out when the current install was installed?"
date: 2009-08-20
forum: General Help
---

### Post by morbid_bean on 2009-08-20
What I want to accomplish is to find out when exactly my current install of ubuntu was installed....there has to be some way.

---

### Post by dhughes on 2009-08-20
From what I can see from a Google search it appears there is not any, and I could be wrong, simple or elegant answer that ends up like "Aug 18, 2008 15:31"

 Although, this: [http://ubuntuforums.org/archive/index.php/t-1029921.html](http://ubuntuforums.org/archive/index.php/t-1029921.html)

 suggests you try this:

 ```
sudo cat /var/log/installer/syslog | less
```

 And look at the date (on the left), press q to quit.

---

### Post by oboedad55 on 2009-08-20
> **dhughes said:**
> From what I can see from a Google search it appears there is not any, and I could be wrong, simple or elegant answer that ends up like "Aug 18, 2008 15:31"

 Although, this: [http://ubuntuforums.org/archive/index.php/t-1029921.html](http://ubuntuforums.org/archive/index.php/t-1029921.html)

 suggests you try this:

 ```
sudo cat /var/log/installer/syslog | less
```

 And look at the date (on the left), press q to quit.

This works. I get an install date of July 30, which is about right.

---

### Post by morbid_bean on 2009-08-20
```
 Apr 26 09:58:22 ubuntu syslogd 1.5.0#2ubuntu6: restart.
Apr 26 09:58:22 ubuntu kernel: Inspecting /boot/System.map-2.6.27-7-generic
Apr 26 09:58:23 ubuntu kernel: Cannot find map file.
Apr 26 09:58:23 ubuntu kernel: Loaded 50186 symbols from 105 modules.
Apr 26 09:58:23 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 26 09:58:23 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 26 09:58:23 ubuntu kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
Apr 26 09:58:23 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ff0000 (usable)
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000017ff0000 - 0000000017ff8000 (ACPI data)
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000017ff8000 - 0000000018000000 (ACPI NVS)
Apr 26 09:58:23 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 000: 
```
............

Looks good to me!! THANKS A BUNCH!

---

