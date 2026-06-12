---
title: "Grub issues"
date: 2010-02-07
forum: General Help
---

### Post by igriego on 2010-02-07
I have two partitions on the same drive that both boot some variation of Ubuntu but the wrong /boot/grub/menu.lst file is being read is there a way that I can the preferred /boot/grub/menu.lst file to be read come boot time? Should I just remove that partition I never really use and there is not any important files on there anyway

---

### Post by warp99 on 2010-02-07
You need to run grub-setup and change the boot partition to the menu.lst you want. A command like this is needed:

```
sudo grub-setup hd0,1
```

In this example 0 is the first drive and 1 is the second partition. Change these numbers to reflect your hardware.

Edit: Here's some more information on the process:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by igriego on 2010-02-07
All yes exactly I went ahead a erased the old partition and the rebooted to get a Error: 22 but configuring it like you said is the right way to go so I had to do that from a love usb. But that's correct so his is officially [Solved]

---

