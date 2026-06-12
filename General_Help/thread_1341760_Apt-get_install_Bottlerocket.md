---
title: "Apt-get install Bottlerocket"
date: 2009-11-30
forum: General Help
---

### Post by OpenJohnson on 2009-11-30
I've been trying to set up some x10 devices around the house. I used apt-get install bottlerocket to set up a command line program. After installing Bottlerocket, it worked perfectly. However, after restarting the computer. It could no longer find the directory when ran the same commands. 

Essentially, it no longer works after re-boot. Any ideas why this would happen?

---

### Post by peter3 on 2010-05-13
After a reboot, the /dev/firecracker symbolic link that points to your
serial port disappears.  I'm working on a way to make it stay around,
but have not (re)found it yet.  Soon....

---

