---
title: "Help"
date: 2006-06-07
forum: General Help
---

### Post by farid02 on 2006-06-07
I have the Ubuntu 5.10 alongwith Windows XP Home and the Suse 10 on one 80 GB Hard Disk with Multiboot ( Grub ).
Today when I got updates os SuSE and rebooted the system I was not able to start Ubuntu. After showing the Ubuntu logo it gives a message that unable to boot dropping to shell. Then nothing happens.
I am quite new with linux based systems and need help in rwestoring by Ubuntu Operating system.
Any assistance given will be highly appreciated.
Thanks & Regards,

Farid Ansari
Karachi, Pakistan

---

### Post by terminatorkobold on 2006-06-07
Hello,

Is your grub menu.lst file in your Suse partition or in your ubuntu partition? If it is in the partition with suse, it is possible that suse changed your configuration file. Check the line about booting ubuntu, it should look like this:

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

where (hd0,4) is the partition wit ubuntu in ''grub syntax''

I hope it helps!

---

### Post by tonyr on 2006-06-07
I don't know anything about Suse, but I assume that if you are using **grub**, there
is a file **menu.lst** or **grub.menu** somewhere in your Suse file system.  
In Ubuntu it is **/boot/grub/menu.lst**.  Find that and post it here.

Also tell in what order you installed the OSes, and how your disk is partitioned.
In a terminal do
```

fdisk -l /dev/hda

```
and poet the output here.

When you install Ubuntu (and probably Suse), if you let it install **grub**,
it changes the **grub** boot information.  Ubuntu is usually smart enough
to find all bootable OS and do the right thing.  SInce  don't know anything
about Suse, I can't say anything about what it does.

---

