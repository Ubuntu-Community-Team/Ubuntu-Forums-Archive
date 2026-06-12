---
title: "help reinstalling grub 2 over mbr"
date: 2012-09-01
forum: General Help
---

### Post by exkend on 2012-09-01
Hello, 

Could any of you kind people help me reinstall grub2 over windows 7 mbr? I have tried reinstalling ubuntu 12.04 but I get no boot loader, instead it just goes straight to windows 7.

Thanks for reading.

---

### Post by jerome1232 on 2012-09-01
Does this help?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by exkend on 2012-09-01
Hi thanks for the reply. Unfortunately this didn't work. It's strange..

Thanks again

---

### Post by oldfred on 2012-09-01
Did you use Boot-Repair from jerome1232's link?

Post the BootInfo report link that it creates, so we can see details of your install.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by dcstar on 2012-09-01
> **exkend said:**
> Hello, 

Could any of you kind people help me reinstall grub2 over windows 7 mbr? I have tried reinstalling ubuntu 12.04 but I get no boot loader, instead it just goes straight to windows 7.

Thanks for reading.

Boot off Live CD, then:

```
sudo dpkg-reconfigure grub-pc
```

And select the device that your system actually boots off for the bootloader location.

Boot up your proper Ubuntu system and then repeat the procedure.

---

### Post by exkend on 2012-09-02
Hi David, 

 Thanks for the reply, I tried your code with no luck. I appreciate your help anyway.

---

