---
title: "Mount of system failed"
date: 2009-12-15
forum: General Help
---

### Post by Ina de Beer on 2009-12-15
Can somebody please help me?

I'm using Ubuntu 9.10 and when I start my computer it says :

Mount of system failed.
20d026-aab2-4bf4-87a8-f3c9acad0fd9  
A maintenance shell will now be started.  
Control - D will terminate this shell and re-try.  
root@ina:

It doesn't do anything else and doesn't start up.

---

### Post by lmarmisa on 2009-12-15
This seems a problem while trying to mount a partition with a bad UUID.

You can see your disks and partitions typing this command

```

fdisk -l

```This command shows the UUIDs of the different partitions

```

blkid

```And this commad shows you the /etc/fstab file, where are defined the automatic mounting commands at startup:

```

cat /etc/fstab

```

---

### Post by Ina de Beer on 2009-12-18
Dear Imarisma,

Unfortunately that did not solve my problem it only left me with the following:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

