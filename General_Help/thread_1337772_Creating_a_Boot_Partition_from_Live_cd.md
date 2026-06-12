---
title: "Creating a Boot Partition from Live cd"
date: 2009-11-25
forum: General Help
---

### Post by SebastienEndo on 2009-11-25
I have been following the steps from that page:
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
truing to create a boot partition from which grub could run to boot either windows 7 or Ubuntu.

My problem is that I can't edit any of the files on my ubuntu partition because I can't get permission and I can't boot in either windows or ubuntu ...

gedit mnt/root/ect/fstab

won't work...

what should I do?

---

### Post by mechro on 2009-11-25
post deleted... I'm writing rubbish!


Is it as simple as ect should be etc?

---

### Post by SebastienEndo on 2009-11-26
> **mechro said:**
> post deleted... I'm writing rubbish!


Is it as simple as ect should be etc?

wow, I am very stupid, that worked,
it might be my exams coming up next weeks...
Thanks !

---

### Post by SebastienEndo on 2009-11-26
ok I got two more problems now,
I search arround and can find an answer,

1. the /boot/grub directory doesn't have a menu.lst
2. when I type   sudo grub   I get "command not found" and whne I type just  grub, I get "grub is not currently installed, you can install it with apt-get"

any idea?

---

### Post by mechro on 2009-11-26
You're using an old tutorial which refers to legacy Grub. If you're running Ubuntu 9.10 then you're using Grub2 which doesn't have a menu.lst file. It has a grub.cfg file but you shouldn't edit that. You have to edit it using Grub2's other files and procedures.

I don't know how to convert the tutorial's instructions to work with Grub2. Perhaps these links may help...

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

