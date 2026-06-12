---
title: "Update Persistent Live USB?"
date: 2010-10-10
forum: General Help
---

### Post by DOS Boot on 2010-10-10
Should Linux distributions running on persistent Live USBs be updated? 

Also, could someone who is using a persistent Live USB of Ubuntu 10.04 use the update manager to upgrade to 10.10?

---

### Post by JackNocturne on 2010-10-10
I don't know if they should be updated.

But
**Yes**,someone using persistent Live USB can update as long as there is **enough** free space.:P

---

### Post by C.S.Cameron on 2010-10-10
If you want to do updates and upgrades, do a Full install to your flash drive.

Upgrading on a persistent drive will quickly fill it.
The kernel is part of an image file that can't be updated.

The best you can do is put your home directory in it's own partition, (named home-rw), then when upgrading to a new version you don't loose too much data.

---

