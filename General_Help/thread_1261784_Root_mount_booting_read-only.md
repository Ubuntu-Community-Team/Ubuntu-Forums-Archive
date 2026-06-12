---
title: "Root mount booting read-only"
date: 2009-09-09
forum: General Help
---

### Post by Jorsher on 2009-09-09
Hello :)

I have a Kimsufi server with Ubuntu 8.04 installed.

I was trying to set up disk quotas and in one of the links I found online, was told to remount the root directory with "ro,remount."

Little did I know, this sets it to read-only.

Now, whenever I boot it's set to read-only and I cannot write to files even as root.  I cannot install apps, write to files, or run nxmachine until I do "mount -o remount -t /sda1 /dev/sda1 /"

When I restart, it's back to read-only.

I've tried editing the fstab file to "defaults,rw,bootfs,usrquota" and it still will boot as read only.

How can I fix this?

Or, is it possible to have it reinstall the OS or revert back to the original installation without changing my passwords remotely?

Thanks!

---

### Post by Jorsher on 2009-09-09
I have also edited lilo.conf and removed the read-only line on /dev/sda1 and it still boots as read-only.

:(

---

### Post by hal10000 on 2009-09-09
Have you tried sudo mount / -o remount,rw ?
btw., you should not remove the read-only flag in your lilo.conf, this ro flag is just in use during boot process and when boot process ends, it is set to read-write.

---

### Post by Jorsher on 2009-09-09
> **hal10000 said:**
> Have you tried sudo mount / -o remount,rw ?
btw., you should not remove the read-only flag in your lilo.conf, this ro flag is just in use during boot process and when boot process ends, it is set to read-write.

Yes I tried that and it wouldn't do the command.  I would get this:

> mount: / not mounted already, or bad option

I also tried repairing the MBR manually and, well, it wouldn't let me log in remotely anymore after I rebooted ;)

I reinstalled and everything is fresh again.

I now have a new issue!

---

