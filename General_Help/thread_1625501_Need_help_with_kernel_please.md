---
title: "Need help with kernel please"
date: 2010-11-19
forum: General Help
---

### Post by Jolicoeur on 2010-11-19
I just checked my kernel version in 10.10 and it is 22.6.35, should it not be 2.6.36?  I thought that this was updated automatically? Is it something I need to do manually?

Thanks

---

### Post by Hippytaff on 2010-11-19
You can do
```

sudo apt-get dist-upgrade

```
for the next alpha version which probably has a newer kernel.
 
EDIT -> Ignore this moment of babling insanity

---

### Post by deanjm1963 on 2010-11-19
10.10 is built around the 2.6.35 kernel and will receive updates to that kernel. Newer versions of Ubuntu will have newer kernels. You can install a newer kernel into 10.10 if you really want or need to. There are many threads on updating to a newer kernel version.

---

### Post by coffeecat on 2010-11-19
> **Jolicoeur said:**
> I just checked my kernel version in 10.10 and it is 22.6.35, should it not be 2.6.36? 

No, the kernel in Maverick is 2.6.35, unless you've backported a kernel or used a PPA repo.

---

### Post by a-user on 2010-11-19
ubuntu 10.10 has kernel 2.6.35. as far as i know you never get newer mainline version during the lifetime of an ubuntu release. thee will only be updates to 2.6.35, but it will not be 2.36 or newer.

and don't do a distupgrade if you don't wont to become alpha tester for ubuntu 11.04

---

### Post by Hippytaff on 2010-11-19
> **Hippytaff said:**
> You can do
```

sudo apt-get dist-upgrade

```
for the next alpha version which probably has a newer kernel.
 
Actually I don't think 11.04 alpha is available yet and it's not advisable to use it unless you want to be an alpha tester...
 
I think I'm getting confused...I thought dist-upgrade would install a new kernel if one was available, sure I've done this before :-s

---

### Post by coffeecat on 2010-11-19
> **Hippytaff said:**
> I think I'm getting confused...I thought dist-upgrade would install a new kernel if one was available, sure I've done this before :-s

You're not the only one. For ages I kept getting dist-upgrade muddled with upgrade-manager -c. From man apt-get:

> dist-upgrade
in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packagesFrom man upgrade-manager:

> -c, --check-dist-upgrades
    Check if a new distribution release is available"--check-dist-upgrades"? I think the devs have been playing fast and loose with terminology. No wonder lesser mortals get confused. :-k

---

### Post by Hippytaff on 2010-11-19
Thanks coffee cat, I did a dist-upgrade last night and didn't reboot, just shutdown. I hope I haven't got 11.04 alpha installed when I get home :-s

---

### Post by coffeecat on 2010-11-19
> **Hippytaff said:**
> Thanks coffee cat, I did a dist-upgrade last night and didn't reboot, just shutdown. I hope I haven't got 11.04 alpha installed when I get home :-s

I don't think so. I hope not! :? As far as I can tell, dist-upgrade is only needed when dependencies are out of sync in the repos and that only happens in the pre-release testing phase. General advice in testing pre-releases is not to do a partial upgrade if offered one with Upgrade Manager or you'll have a horribly broken system, and to use 'sudo apt-get dist-upgrade' rather than 'sudo apt-get upgrade' to do a safe upgrade of packages that need updating. Upgrade here meaning updating packages for which newer versions are available. I've never had occasion to need or use 'dist-upgrade' in a release version. I don't even know if the need would ever arise.

The problem seems to be, at least for me, the ambiguity around the word 'upgrade'. Upgrade a package or upgrade a release?

---

### Post by Hippytaff on 2010-11-19
Phew - thanks again :-) I'm ok to use dist-upgrade to fix dependencies and upgrade packages...I'll get my head around this yet :-D
 
(And I think I've Hijacked your thread Jolicour :-s sorry :-D )

---

### Post by oldos2er on 2010-11-19
> **Hippytaff said:**
> Thanks coffee cat, I did a dist-upgrade last night and didn't reboot, just shutdown. I hope I haven't got 11.04 alpha installed when I get home :-s

You'll need to do more than that if you want 11.04; dist-upgrade has nothing to do with upgrading to a newer release.

---

### Post by Hippytaff on 2010-11-19
I know now...I panicked :-D

---

