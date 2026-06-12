---
title: "/dev/sda and /dev/sdb switching after upgrade"
date: 2011-03-03
forum: General Help
---

### Post by Klunk on 2011-03-03
I have recently upgraded my stable 10.04 to 10.10 (I know if its not broken leave it alone)

Ever since I have done that my drive assignments seem to switch. Sometimes it boots OK and others it fails to find the partitions to mount /home and another mount point. This is because sometimes the ATA disk with ubuntu installed is /dev/sdb (wrong) and others it correctly gets assigned to /dev/sda and it can then mount the partitions 1 and 2 for /home and the other mount point.

What determines the assignments and how can I stop it going wrong. It normally fails on the first boot and if I reboot will come back fine.

---

### Post by sanderd17 on 2011-03-03
I don't know why it fails, but in your /etc/fstab file, you could use the UUID of the harddisks instead of the names /dev/sda and others.

Search the internet for some "automatic mouting" tutorials and compare the lines they add to the fstab file.

---

### Post by Klunk on 2011-03-03
oh, that would work, thanks. / is mounted using the uuid, I didnt think of that.

EDIT: I have just used **tune2fs -l** to find the UUID of the 2 partitions and unmount followed by mount of the non /home one works a treat.

---

