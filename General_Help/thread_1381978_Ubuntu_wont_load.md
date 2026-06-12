---
title: "Ubuntu wont load?"
date: 2010-01-15
forum: General Help
---

### Post by demonic_crow on 2010-01-15
I just did an update from the manager and restarted it and this what I get.
 
init: mountall main process (397) terminated with status 3 
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@Home:~#

---

### Post by spcwingo on 2010-01-15
From that prompt run:

```
fdisk -l
```

On one of the partitions it should say under system "Linux".  Note the device designation (ex /dev/sda2).  Then you can try:

```
fsck /dev/sda2
```

Or whatever device designation you got from the first step.

---

### Post by demonic_crow on 2010-01-15
Wow, thanks that worked.  It also got rid of a mounting issue that would show up while booting after I updated to Ubuntu 9.10.

---

### Post by spcwingo on 2010-01-15
I'm glad you got it going.

---

### Post by jward3010 on 2010-01-15
> **demonic_crow said:**
> Wow, thanks that worked.  It also got rid of a mounting issue that would show up while booting after I updated to Ubuntu 9.10.
It'd be great if you marked this thread SOLVED now, go to "Thread Tools" towards the top and pick "SOLVED" option.

---

