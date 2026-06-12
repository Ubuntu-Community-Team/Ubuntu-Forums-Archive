---
title: "EEEPC disk missing?"
date: 2009-11-14
forum: General Help
---

### Post by majest on 2009-11-14
I installed 9.10 on my EEEPC 1000 a few days ago. All is going well. However, there should be an 8GB sollid state drive and a 32GB drive. When I type df -h from the command line I don't see the 32GB one.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.1G  2.7G  4.1G  40% /
udev                  498M  260K  497M   1% /dev
none                  498M  188K  497M   1% /dev/shm
none                  498M   80K  498M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw

Can someone explain what is going on there???

---

### Post by undecim on 2009-11-14
The 32G volume is not mounted. If you run

sudo fdisk -l | grep "Disk /dev/" 

Do you see it there?

---

### Post by majest on 2009-11-16
> **undecim said:**
> The 32G volume is not mounted. If you run

sudo fdisk -l | grep "Disk /dev/" 

Do you see it there?

Yes - I see it there,

Disk /dev/sda: 8069 MB, 8069677056 bytes
Disk /dev/sdb: 32.3 GB, 32279224320 bytes

That's a relief :) I'm wondering, does this mean it's being used?

---

