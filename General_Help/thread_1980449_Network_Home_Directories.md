---
title: "Network Home Directories"
date: 2012-05-15
forum: General Help
---

### Post by afflux on 2012-05-15
Hi there,

I'm trying to install some ubuntu precises machines in a pc-lab using libnss-ldapd and libpam-krb5, to provide the user accounts from our windows active directory. We also need to have the same home directory (hosted on a windows machine as well) for each user, regardless on which machine he logs into.

I tried implementing this using cifs and nfs4 - and if they work at all (had some issues with KDE over cifs - probably locking related), [the dconf applications don't seem to be able to remember their settings](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448) (I used empathy for testing, not sure how the other applications behave).

Since I assume I'm not the only one trying to have remote home directories, I'd like to know what's the best way to achieve this.

Edit: this account is old and unused - it seems I can't change my profile info. I'm certainly not on feisty testing ;)

---

### Post by dcstar on 2012-05-15
> **afflux said:**
> Hi there,

I'm trying to install some ubuntu precises machines in a pc-lab using libnss-ldapd and libpam-krb5, to provide the user accounts from our windows active directory. We also need to have the same home directory (hosted on a windows machine as well) for each user, regardless on which machine he logs into.

I tried implementing this using cifs and nfs4 - and if they work at all (had some issues with KDE over cifs - probably locking related), [the dconf applications don't seem to be able to remember their settings](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448) (I used empathy for testing, not sure how the other applications behave).

Since I assume I'm not the only one trying to have remote home directories, I'd like to know what's the best way to achieve this.

Edit: this account is old and unused - it seems I can't change my profile info. I'm certainly not on feisty testing ;)

/home is a Linux System folder that requires a Linux filesystem. Non-Linux filesystems do not support the required Linux attributes and features.

Use NFS or another Linux compatible network file access.

---

### Post by Bucky Ball on 2012-05-15
> **afflux said:**
> 

Edit: this account is old and unused - it seems I can't change my profile info. I'm certainly not on feisty testing ;)

Welcome back. I think a new forum rule is that you need fifty posts before you can start changing things with your profile. ;)

---

### Post by afflux on 2012-05-18
> **dcstar said:**
> Use NFS

> **afflux said:**
> 
I tried implementing this using cifs and **nfs4** - [...] the dconf [applications don't seem to be able to remember their settings](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448)

Also note that both the LP and the upstream bug are titled "[dconf doesn't] support NFS".

> **dcstar said:**
> or another Linux compatible network file access.
Such as?

---

