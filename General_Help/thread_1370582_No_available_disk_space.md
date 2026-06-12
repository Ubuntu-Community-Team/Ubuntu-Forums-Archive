---
title: "No available disk space"
date: 2010-01-02
forum: General Help
---

### Post by ketom2000 on 2010-01-02
I am running Hardy (8.04). AMD-64.

When I check under the system monitor, under system status I see Available disk space: 0 bytes.

If I check under nautilus I see that I have 74.5 GB free.

When run df -h this is what I get.

Filesystem            Size  Used Avail Use% Mounted on
varrun                944M  272K  944M   1% /var/run
varlock               944M     0  944M   0% /var/lock
udev                  944M   64K  944M   1% /dev
devshm                944M   12K  944M   1% /dev/shm
lrm                   944M   45M  900M   5% /lib/modules/2.6.24-26-generic/volatile
/dev/sda1              57G   44G   11G  82% /media/multi
/dev/sdd1             932G  396G  536G  43% /media/HOPPY LABEL

I don't understand what is going on.  Cleaning up my home folder isn't making any difference.  Where do I look for the files that are clogging up my system?

---

### Post by gordintoronto on 2010-01-02
Normally df will show the root partition and maybe /home if it is a separate partition.  Seeing /media/multi is completely unexpected.  Did you run a mount command to create /media/multi?

---

### Post by ketom2000 on 2010-01-02
The media share is mounted in fstab

---

