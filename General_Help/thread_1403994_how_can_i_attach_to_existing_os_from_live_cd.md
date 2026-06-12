---
title: "how can i attach to existing os from live cd"
date: 2010-02-10
forum: General Help
---

### Post by aviramof on 2010-02-10
to try to fix it from there with the command  chmod?

and what commands might help me fix the problem?

thanks in advance.

---

### Post by flippo on 2010-02-10
To mount the filesystem from a live cd you have to make a directory then use the mount command, something like this:

sudo mkdir /mnt/myfs
sudo mount /dev/<device> /mnt/myfs

The contents of the filesystem will then be in /mnt/myfs

Example:
My HD is on /dev/sda, and my Linux root partition is /dev/sda4, so I do
sudo mkdir /mnt/rootfs
sudo mount /dev/sda4 /mnt/rootfs

---

### Post by aviramof on 2010-02-11
thank you very much

---

