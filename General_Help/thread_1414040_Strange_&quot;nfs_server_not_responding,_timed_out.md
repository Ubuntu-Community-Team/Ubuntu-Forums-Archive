---
title: "Strange &quot;nfs: server not responding, timed out&quot; on Ubuntu workstartion, only mornings"
date: 2010-02-23
forum: General Help
---

### Post by Master One on 2010-02-23
I have set up nfs-kernel-server on my Debian Lenny server and nfs-common on my Ubuntu 9.10 workstation as described [here](https://help.ubuntu.com/community/SettingUpNFSHowTo).

Everything is generally working just fine, except that every time, when I start my workstation from suspend-to-RAM after more than a couple of hours of suspension, I can not access the NFS-shares (nautilus or ls in a terminal just hangs), and /var/log/messages shows "nfs: server *NAME-OF-SERVER*not responding, timed out".

The problem is definitely not the server, because all I need to do to get it working again, is "umount -f /mnt/*NFS-SHARE*" followed by "mount /mnt/*NFS-SHARE*", or just wait some time (around 10-15 minutes) and then everything is fine again.

I always only suspend-to-RAM, I usually do not turn of the machine completely. I have no explanation for that issue, but it must have something to do with being in suspend-to-RAM for a certain time. Pretty weird!

Anybody any idea?

Strangely I never had this problem with NFS shares from a server running the FreeBSD-based FreeNAS operating system.

Should the NFS shares be unmounted before suspension, and mounted after resume? Can this be done automatically?

---

### Post by Master One on 2010-03-02
Nobody else using NFS with Ubuntu?

---

### Post by darklebrock on 2010-04-28
Hi ...

I'm having the exact same problem and did not figure out how to sort it.

I even installed a backported kernel on the Debian nfs server, to see if the problem could be the server. Now i'm using a 2.6.30 and this problem remains.

I have it with many Ubuntu clients. one running on a x86-64 Desktop 9.10 and another on a macbook (9.10 as well).

We'll see if Lucid fix that issue...

Regards

Yvan

---

