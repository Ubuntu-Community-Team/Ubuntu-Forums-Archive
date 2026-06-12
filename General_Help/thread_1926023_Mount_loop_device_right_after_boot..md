---
title: "Mount loop device right after boot."
date: 2012-02-15
forum: General Help
---

### Post by iX9 on 2012-02-15
Is some-how possible do this, just after boot?

**losetup /dev/loop0 /X**

Need to solve this situation:
I need to have all linux parts just on the one partition (/dev/sda1, ext4) **- AND -** to have fully encrypted system.

Normally, there must be other (unencrypted) partition for /boot.
Maybe I found the way?

I have /boot on this partition and the rest of the system - in LUKS encrypted file-container placed as file in the root of the same partition.

Only one thing I cant solve - how to tell to the core, to "make device" from file by losetup.
It must be done **after** boot, but **before** the cryptsetup asks for password.

---

### Post by Lars Noodén on 2012-02-15
You can put things in /etc/rc.local and they will run at startup just after all the SystemV scripts have run.

---

### Post by iX9 on 2012-02-15
I dont thing so, I cant put it to /etc/rc.local, because this file is encrypted in the file container with rest of the system.
First it must be unlocked, then it can be readed.
But for unlocking, I need "make file as device" first - it does that losetup command.
Or am I wrong?

---

### Post by iX9 on 2012-02-16
Maybe do some magic with initramfs?
There is directory /etc/initramfs-tools/scripts/premount...
"Premount" - maybe it mean run something before mount root filesystem?

---

