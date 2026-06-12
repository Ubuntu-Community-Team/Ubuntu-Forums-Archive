---
title: "How to Access Missing Ubuntu Root Drive"
date: 2011-02-07
forum: General Help
---

### Post by Kanshu on 2011-02-07
The file in /dev/disk/by-uuid went missing and I can't boot up to my Ubuntu drive. I can however see the Ubuntu partition from my Kubuntu partition.

How do I restore the missing file from the prompt? What commands to I use?

---

### Post by dcstar on 2011-02-08
> **Kanshu said:**
> The file in /dev/disk/by-uuid went missing and I can't boot up to my Ubuntu drive. I can however see the Ubuntu partition from my Kubuntu partition.


It is not a "file", it is a generated device created by the kernel when it detects the device.

If you have changed the partition then the UUID will have changed, make sure the actual UUID value in your /etc/fstab file matches what the actual partition is.

---

### Post by Kanshu on 2011-02-08
> **dcstar said:**
> It is not a "file", it is a generated device created by the kernel when it detects the device.

If you have changed the partition then the UUID will have changed, make sure the actual UUID value in your /etc/fstab file matches what the actual partition is.

First of all, I didn't change the partition. I just switched over to another O/S to work on a different matter and when I tried to access Ubuntu after that, it tells me that the Ubuntu root drive with a particular UUID is missing.

I may have fixed a similar problem in the past so I'm familiar with the solution being a simple matter. I just don't know the specific shell commands to use.

Anyway, I know the exact UUID because the system is saying me that it is missing. Incidentally, I could list (using ls command from the shell) the /dev/disk/by-uuid folder but I could not see the /disk or /disk/by-uuid folders from Kubuntu--my other working O/S.

---

