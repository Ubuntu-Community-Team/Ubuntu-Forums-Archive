---
title: "Hard drive almost full - clears at reboot"
date: 2010-02-24
forum: General Help
---

### Post by qprfact on 2010-02-24
I am running Ubuntu on a home server, which has three drives - the boot drive of 120GB, another media drive of 120GB, and a third media drive of 1TB.

The boot drive contains the OS and all the programs and settings, and about 45-50GB of data, so should have plenty of free space.

But I am finding the free space keeps falling and falling - to the extent that I am getting low disk space warnings, and last night was down to only 956MB free!

I tried in vain to see where the space was being taken up, but to no avail. So I rebooted. And then immediately had 50GB free.

So something in the reboot process is clearing whatever is clogging up my machine. How can I fix this without resorting to a reboot? Preferably by it not clogging up in the first place!

Thanks in advance

---

### Post by dcstar on 2010-02-24
> **qprfact said:**
> I am running Ubuntu on a home server, which has three drives - the boot drive of 120GB, another media drive of 120GB, and a third media drive of 1TB.

The boot drive contains the OS and all the programs and settings, and about 45-50GB of data, so should have plenty of free space.

But I am finding the free space keeps falling and falling - to the extent that I am getting low disk space warnings, and last night was down to only 956MB free!

I tried in vain to see where the space was being taken up, but to no avail. So I rebooted. And then immediately had 50GB free.

So something in the reboot process is clearing whatever is clogging up my machine. How can I fix this without resorting to a reboot? Preferably by it not clogging up in the first place!

Thanks in advance

Check the log files.

---

### Post by qprfact on 2010-02-24
How do I do that please?

---

### Post by plucky on 2010-02-24
> **qprfact said:**
> How do I do that please?

From a terminal ```
ls -lh /var/log
``` and look for very large files.

Also post output of ```
df -h
```

Check you haven't got a backup process running in the background.

Good Luck

---

### Post by qprfact on 2010-03-08
It was a logging issue - I had way too much logging in my iptables!

---

