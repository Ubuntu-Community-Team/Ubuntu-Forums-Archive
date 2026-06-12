---
title: "OGLE: msgget ipc_creat failed: No space left on device"
date: 2006-02-19
forum: General Help
---

### Post by bkanuka on 2006-02-19
When I run ogle I get:
```
*ctrl: msgget ipc_creat failed: No space left on device
```
df says:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc3             36139752  17649952  17021140  51% /
tmpfs                   518324         0    518324   0% /dev/shm
tmpfs                   518324     12588    505736   3% /lib/modules/2.6.12-10-386/volatile
/dev/hdc2               293586     30010    247913  11% /boot
/dev/hdd2             75686132  58114448  13664276  81% /Linuxdocs
/dev/scd0              3752904   3752904         0 100% /media/cdrom1

```
/dev/shm is writeable
ipcs runs about 233 lines of output (don't know what this means, but I think it's bad)

Any Ideas?

---

### Post by bkanuka on 2006-02-21
I know its only been two days but..................BUMP!

---

### Post by bkanuka on 2006-02-26
This is pretty important. Does anyone have any idea?

---

### Post by bkanuka on 2006-06-05
Just to let you know, all I had to do was restart my computer.  However, I like Totem better now; it does the same things and more.

---

