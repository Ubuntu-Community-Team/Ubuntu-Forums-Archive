---
title: "Ubuntu doesn't boot with LILO"
date: 2009-08-19
forum: General Help
---

### Post by Dannik on 2009-08-19
I am using Slackware and have LILO as my bootloader. I also have Ubuntu on my /dev/sda2 and want to be able to boot it too. This is what I did:

1. Mount /dev/sda2 to /mnt/Ubuntu
2. Add this to my /etc/lilo.conf
```

image = /mnt/Ubuntu/boot/vmlinuz-2.6.27-7-generic
root = /dev/sda2
label = Ubuntu
read-only

```
3. Run lilo.

When I restart and try to boot Ubuntu I get a black screen and have to restart my computer. Can you suggest anything? The Ubuntu partition has an initrd image in its /boot directory, maybe I need to include it too?

---

### Post by Dannik on 2009-08-19
Solved it. I had to add the initrd image. This is what the final addition looks like:

```

image = /mnt/Ubuntu/boot/vmlinuz-2.6.27-7-generic
  root = /dev/sda2
  label = Ubuntu
  initrd = /mnt/Ubuntu/boot/initrd.img-2.6.27-7-generic
  read-only

```

Sorry to bother.

---

### Post by andrew.46 on 2009-08-19
Hi Dannik,

This is the exact issue i wrestled with a while back. If you want to see the discussion and some solutions have a look here:

Advice for Lilo setup: Dual Boot Slackware / Ubuntu
[http://www.linuxquestions.org/questions/slackware-14/advice-for-lilo-setup-dual-boot-slackware-ubuntu-613632/](http://www.linuxquestions.org/questions/slackware-14/advice-for-lilo-setup-dual-boot-slackware-ubuntu-613632/)

Mind you I have switched to virtualbox since that time which is another excellent option to consider.

Andrew

---

