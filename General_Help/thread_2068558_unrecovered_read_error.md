---
title: "unrecovered read error"
date: 2012-10-09
forum: General Help
---

### Post by cybercity@localhost on 2012-10-09
hi friends i need your help. my kernel is continuously logging an strange error in my messages file. have a look at this message.
```

Oct  9 19:23:28 cybercity kernel: [10140.008047]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:28 cybercity kernel: [10140.008056]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:30 cybercity kernel: [10142.002668] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:30 cybercity kernel: [10142.003299] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:30 cybercity kernel: [10142.003862] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:30 cybercity kernel: [10142.003968] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:30 cybercity kernel: [10142.003972]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:30 cybercity kernel: [10142.003981]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:30 cybercity kernel: [10142.004658] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:32 cybercity kernel: [10144.000687] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:32 cybercity kernel: [10144.001217] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:32 cybercity kernel: [10144.001799] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:32 cybercity kernel: [10144.001869] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:32 cybercity kernel: [10144.001874]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:32 cybercity kernel: [10144.001882]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:32 cybercity kernel: [10144.002322] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:34 cybercity kernel: [10146.001932] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:34 cybercity kernel: [10146.002464] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:34 cybercity kernel: [10146.009912] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:34 cybercity kernel: [10146.010022] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:34 cybercity kernel: [10146.010025]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:34 cybercity kernel: [10146.010031]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:34 cybercity kernel: [10146.010409] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:36 cybercity kernel: [10148.002633] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:36 cybercity kernel: [10148.003172] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:36 cybercity kernel: [10148.003795] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:36 cybercity kernel: [10148.003901] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:36 cybercity kernel: [10148.003905]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:36 cybercity kernel: [10148.003913]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:36 cybercity kernel: [10148.005066] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:38 cybercity kernel: [10150.003513] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:38 cybercity kernel: [10150.005801] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:38 cybercity kernel: [10150.006885] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:38 cybercity kernel: [10150.006944] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:38 cybercity kernel: [10150.006974]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:38 cybercity kernel: [10150.006983]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:38 cybercity kernel: [10150.007417] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:40 cybercity kernel: [10152.002638] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:40 cybercity kernel: [10152.003179] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:40 cybercity kernel: [10152.011613] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:40 cybercity kernel: [10152.012159] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:40 cybercity kernel: [10152.012999] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:40 cybercity kernel: [10152.013002]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:40 cybercity kernel: [10152.013009]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:42 cybercity kernel: [10154.004304] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Oct  9 19:23:42 cybercity kernel: [10154.004858] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct  9 19:23:42 cybercity kernel: [10154.005452] sr 3:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Oct  9 19:23:42 cybercity kernel: [10154.005570] sr 3:0:0:0: ioctl_internal_command return code = 8000002
Oct  9 19:23:42 cybercity kernel: [10154.005574]    : Sense Key : Medium Error [current] [descriptor]
Oct  9 19:23:42 cybercity kernel: [10154.005582]    : Add. Sense: Unrecovered read error - auto reallocate failed
Oct  9 19:23:42 cybercity kernel: [10154.006117] sr 3:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00

```any idea?

---

### Post by sienile on 2012-10-09
Not sure, but it seems you may have a bad sector or failing HDD.

Use this link to run a few checks on it. [http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/")

---

