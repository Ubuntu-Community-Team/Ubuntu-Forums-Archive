---
title: "and suddently goes black!!!"
date: 2011-11-24
forum: General Help
---

### Post by Krakken on 2011-11-24
Hi community,
My eeepc 1215N with ubuntu 11.04 installed has been working smoothly for monts and suddently this morning went black!!! No ways to make it boot with any kernel o recovery mode. I tried to boot with --single verbose option and the boot stops at :

```
init : plymouth main process (337) executable changed
Init : plymouth main process (337 ) became new process (340 )
Init : plymouth state changed from spawned to post-start
Init : plymouth post-start process (341 )
Init : plymouth state changed from post-start to running
Init : handling started event
``` 

At this line the system hangs forever....


What now?

Thanks
K

---

### Post by LinuxFan999 on 2011-11-24
It looks like your installation of Ubuntu broke itself. The only thing you can do now is back up your data and reinstall Ubuntu.

---

### Post by Krakken on 2011-11-24
Any suggestion on how to recover the data on the desktop an document folder before the reinstall?

Is this issue normal? How can it uppen?

Thanks

---

### Post by LinuxFan999 on 2011-11-24
Sorry for the late reply, but to back up you data, boot from the Ubuntu CD (or USB stick) and select "Try Ubuntu". Once the desktop loads, open nautilus and look for the files you want to back up and transfer them to external storage. Once you are finished, you can reinstall Ubuntu.

---

