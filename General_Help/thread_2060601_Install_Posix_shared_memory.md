---
title: "Install Posix shared memory"
date: 2012-09-20
forum: General Help
---

### Post by Cyber72 on 2012-09-20
Using Ubuntu 12.04. I entered
**mount | grep "shm"**
and terminal returned
**none on /run/[COLOR=Red]shm[/COLOR] type tmpfs (rw,nosuid,nodev)**
Does this mean Posix is not enabled or not installed and what should I do?
I have ATI Radeon Xpress 1150 HyperMemory (integrated). Incidentally this came set at 128MB and probably 512MB would be more suitable - I have 2GB of RAM.

---

### Post by matt_symes on 2012-09-20
Hi

> **Cyber72 said:**
> Using Ubuntu 12.04. I entered
**mount | grep "shm"**
and terminal returned
**none on /run/[COLOR=Red]shm[/COLOR] type tmpfs (rw,nosuid,nodev)**
Does this mean Posix is not enabled or not installed and what should I do?
I have ATI Radeon Xpress 1150 HyperMemory (integrated). Incidentally this came set at 128MB and probably 512MB would be more suitable - I have 2GB of RAM.

shm is shared memory a mounted at /run/shm. I have it on my machine.

```

matthew-Aspire-7540:/home/matthew % mount | grep shm
none on /run/shm type tmpfs (rw,nosuid,nodev)
matthew-Aspire-7540:/home/matthew %
```

```

matthew-Aspire-7540:/home/matthew % ls -ld /run/shm 
drwxrwxrwt 2 root root 160 Sep 20 16:27 /run/shm/
matthew-Aspire-7540:/home/matthew %
```

What do you mean by POSIX not installed ? POSIX is a standard.

Kind regards

---

### Post by Cyber72 on 2012-09-20
You're right thanks

---

