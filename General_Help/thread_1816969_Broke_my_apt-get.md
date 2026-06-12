---
title: "Broke my apt-get"
date: 2011-08-02
forum: General Help
---

### Post by Absol on 2011-08-02
hi, I installed a newer libc6 with dpkg and a few other deb files, now apt-get doesn't work and gives this error:

```

...
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (< 2.13) but 2.13-0ubuntu13 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu10.2) but 2.13-0ubuntu13 is installed
 libnih1 : Depends: libc6 (< 2.13) but 2.13-0ubuntu13 is installed
 libsqlite3-dev : Depends: libsqlite3-0 (= 3.7.2-1ubuntu0.1) but 3.7.4-2ubuntu5 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

when I use:

```
dpkg -l | wc
```

it returns:
1623   14542  215463
so i think i got like 1620 packages conflicted...

Is there a way to fix this without a reinstall?

thanks in advance for your advice

---

### Post by bodhi.zazen on 2011-08-02
> **Absol said:**
> hi, I installed a newer libc6 with dpkg and a few other deb files, now apt-get doesn't work and gives this error:

```

...
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (< 2.13) but 2.13-0ubuntu13 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu10.2) but 2.13-0ubuntu13 is installed
 libnih1 : Depends: libc6 (< 2.13) but 2.13-0ubuntu13 is installed
 libsqlite3-dev : Depends: libsqlite3-0 (= 3.7.2-1ubuntu0.1) but 3.7.4-2ubuntu5 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

when I use:

```
dpkg -l | wc
```

it returns:
1623   14542  215463
so i think i got like 1620 packages conflicted...

Is there a way to fix this without a reinstall?

thanks in advance for your advice

file a bug report on launchpad and wait for a fix =)

Usually these things fix themselves within a day or two at the most.

You could try 

```
sudo apt-get update
sudo apt-get -f
sudo apt-get dist-upgrade
```

---

