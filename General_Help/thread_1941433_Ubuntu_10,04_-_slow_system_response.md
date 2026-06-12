---
title: "Ubuntu 10,04 - slow system response"
date: 2012-03-15
forum: General Help
---

### Post by JackTheKnife on 2012-03-15
Hi,

I have a problem with Ubuntu 10.04. After fixing /boot partition whole system become really slow. To open anything takes some time, even operations from a terminal are slow. System monitoring shows CPU usage between 8-12%.

Any idea what can be wrong?

Thanks

---

### Post by dcstar on 2012-03-16
> **JackTheKnife said:**
> Hi,

I have a problem with Ubuntu 10.04. After fixing /boot partition whole system become really slow. To open anything takes some time, even operations from a terminal are slow. System monitoring shows CPU usage between 8-12%.

Any idea what can be wrong?

Thanks

**Exactly** what did you do to "fix" the /boot partition.

---

### Post by JackTheKnife on 2012-03-16
> **dcstar said:**
> **Exactly** what did you do to "fix" the /boot partition.

I was able to fix /boot partition with gparted and after that I have loaded oldest Grub config with a fix option.

---

### Post by JackTheKnife on 2012-03-16
BTW. When I'm trying to execute:

sudo dpkg --configure -a

I'm getting error:

dpkg: unable to access dpkg status area: Read-only file system

---

### Post by marinara on 2012-03-17
i'd check the file system

---

### Post by JackTheKnife on 2012-03-20
> **marinara said:**
> i'd check the file system

I have done

```
e2fsck -f -y -v
```

on each partition again - no issues found.

---

### Post by JackTheKnife on 2012-03-21
OK, now I'm getting those errors:

Superblock last mount time is in the future
Superblock last write time is in the future

Any clue what is going on? System clock has proper time/date.

---

### Post by dcstar on 2012-03-22
> **JackTheKnife said:**
> I was able to fix /boot partition with gparted and after that I have loaded oldest Grub config with a fix option.

Exactly what did **you** do, what did **you** "fix", explain **everything you did**?

---

### Post by JackTheKnife on 2012-04-23
I run gparted from Ubuntu Live CD and choosed check partition. After that I booted machine to Grub menu and run oldest config where is an option to check filesystem/files (press F)

---

