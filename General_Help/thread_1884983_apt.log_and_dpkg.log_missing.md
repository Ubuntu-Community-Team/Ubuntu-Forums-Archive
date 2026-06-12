---
title: "apt.log and dpkg.log missing"
date: 2011-11-22
forum: General Help
---

### Post by mogliii on 2011-11-22
I could not find the update/installation history on my netbook running Kubuntu 11.10, KDE4.7.3. The graphical package manager showed an empty history.

Digging a bit deeper, I noticed that there is no dpkg.log nor apt.log

```
root@HOST:/var/log# ls -a
.   auth.log  ConsoleKit  dmesg    kdm.log   mail.err  news              syslog  ufw.log
..  boot.log  cups        dmesg.0  kern.log  mail.log  pm-powersave.log  udev    Xorg.0.log
```

I just unistalled two packages using apt-get autoremove, and the two logs appeared. But they only contain the data from this action. So must have gotten lost? how?

Is it possible to find out which packages were installed yesterday without those two? The update broke my wake up from suspend, and I want to find out which one caused this and which one to revert.

---

### Post by mogliii on 2011-11-22
very smart of me:

/etc/fstab:
```
tmpfs /var/log tmpfs defaults,noatime,mode=1777 0 0

```

But this won't fix my suspend trouble. Anyway, at least I know why the logs are gone

---

### Post by matt_symes on 2011-11-22
> **mogliii said:**
> very smart of me:

/etc/fstab:
```
tmpfs /var/log tmpfs defaults,noatime,mode=1777 0 0

```But this won't fix my suspend trouble. Anyway, at least I know why the logs are gone

That made me chuckle. :D

---

