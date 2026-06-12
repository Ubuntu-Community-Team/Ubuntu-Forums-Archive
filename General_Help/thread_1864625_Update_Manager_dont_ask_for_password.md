---
title: "Update Manager dont ask for password"
date: 2011-10-19
forum: General Help
---

### Post by _sAm_ on 2011-10-19
When I use the "Update Manager" on Ubuntu 11.10 it don't ask me for my root password; I can updated as I please. I find it strange since it used to require me to enter my password first, and the app store also require it.

Have they changed it, or is it a bug?

---

### Post by Bluesthang on 2011-10-19
I've noticed the same thing on my end.
And I can't seem to find any settings to to tell it to ask for the password.

---

### Post by owenll on 2011-10-19
According to this thread on launchpad [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/876450](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/876450)

> Starting with Oneiric, users are not required to enter their credentials in order to install security updates from trusted configured archives.

This is a deliberate decision to improve security by having security updates easier to install.

---

