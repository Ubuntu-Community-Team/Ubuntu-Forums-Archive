---
title: "RAID1 best configuration"
date: 2010-04-01
forum: General Help
---

### Post by schifazl on 2010-04-01
Hello!

I'm building a NAS with xubuntu and I've put 2x1,5TB disks in RAID1 with mdadm. My question is really straightforward: do you have any advice for some special tuning/configuration for the RAID setup? Somewhere I read that I should disable disk caching, but I would like to have some more opinions.

Thank you! :)

---

### Post by dcstar on 2010-04-02
> **schifazl said:**
> Hello!

I'm building a NAS with xubuntu and I've put 2x1,5TB disks in RAID1 with mdadm. My question is really straightforward: do you have any advice for some special tuning/configuration for the RAID setup? Somewhere I read that I should disable disk caching, but I would like to have some more opinions.

Thank you! :)

Disabling write caching means the system is more reliable in the case of power failure, but performs slower when writing data.

You have to decide which is more important to you.

---

### Post by schifazl on 2010-04-02
Thanks, I'll make some tests :)

Any other hint?

---

