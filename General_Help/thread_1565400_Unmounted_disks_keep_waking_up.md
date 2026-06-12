---
title: "Unmounted disks keep waking up"
date: 2010-08-31
forum: General Help
---

### Post by SuperDuckk on 2010-08-31
On my desktop, I try to instantly put some disks into sleep using hdparm, for some tests. Though the disks are unmounted, they wake back up in seconds. How can it be? How can I track which process wakes a disk up with what operation?

I think unmount disks should default to standby during system load.

Thank you!

---

### Post by SuperDuckk on 2010-09-01
Looks like it's a bug related with Udev. I've found some info from some years back.

---

### Post by SuperDuckk on 2010-09-02
aha, I think it's about how 'lm-sensors' uses 'hddtemp', probably it  passes -w param to wake up drives those it checks. gotta find a way for  it to check drives only when they are active/idle.

---

