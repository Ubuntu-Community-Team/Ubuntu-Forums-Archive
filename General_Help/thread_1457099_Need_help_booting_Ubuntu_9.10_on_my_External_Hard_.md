---
title: "Need help booting Ubuntu 9.10 on my External Hard Disk"
date: 2010-04-18
forum: General Help
---

### Post by blackice89 on 2010-04-18
Hi, i downloaded and installed Ubuntu 9.10 onto my external hard disk. Everything works great on my desktop. The only problem is, when i have another usb drive connected or when i try to boot it on my laptop, it doesn't work. It keeps returning the message: "Could not find root" or "Could not find sdf2". How do i fix it so it dynamically sets where root is? I kinda need this asap. i did some reading and traced the source of the problem to grub2. Apparently, grub2 doesn't use the device's UUID, and uses the linux directory instead (/dev/sdf2). This means that whenever i plug my E-HDD into a system that has a different number of drives connected to it, i won't be able to boot without editting the boot command. I don't understand it too well but that's what i got from what i read. Is there anyway to fix this?

---

### Post by lidex on 2010-04-18
Did you see this:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435")

---

