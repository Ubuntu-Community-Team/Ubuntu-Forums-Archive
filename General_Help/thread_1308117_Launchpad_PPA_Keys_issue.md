---
title: "Launchpad PPA Keys issue"
date: 2009-10-31
forum: General Help
---

### Post by Uncle Spellbinder on 2009-10-31
The past couple days, Launchpad PPA keys have been nearly impossible to acquire. Of the 6 I use, only one has been able to acquire a key. The rest look like this...

```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7A16627C
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 7A16627C
gpg: requesting key 7A16627C from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

---

### Post by timjohn7 on 2009-10-31
I've experiencedthe same issue... perhaps we need to give the owners time to update?

---

### Post by Uncle Spellbinder on 2009-10-31
> **timjohn7 said:**
> I've experienced the same issue... perhaps we need to give the owners time to update?

You're probably right. Just a bit annoying, but understandable.

---

### Post by laceration on 2009-10-31
I've had that happen before, but it has always been temporary.  It seems like the key servers can not always keep up with demand.  With the new release it is probably a busy time as people are fine tuning their installs with ppa's.

---

### Post by Vaphell on 2009-10-31
[https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193)

alternative servers:
keyserver hkp://subkeys.pgp.net
keyserver hkp://pgp.mit.edu
keyserver hkp://pool.sks-keyservers.net (random server)
keyserver hkp://keys.nayr.net
keyserver [http://keys.gnupg.net](http://keys.gnupg.net)
keyserver [http://wwwkeys.xx.pgp.net](http://wwwkeys.xx.pgp.net) where xx is a two-letter country code.

---

