---
title: "Install Debian side by side w/Ubuntu/Win7"
date: 2010-10-23
forum: General Help
---

### Post by DougieFresh4U on 2010-10-23
Most likely discussed ad nauseam.
Simple question (I hope), I have a triple boot system and would like to add Debian as well. I first installed Win7 then I let partitioner split hard drive when installing Ubuntu. When I installed my second Ubuntu, I let partitioner split the first Ubuntu space in half. When installing Debian, is the installer the same and will it set up another partition and add the entry to grub and not screw everything up (eat my grub menu:mad:)
320GB hard drive:
167GB-Win7
73GB Ubuntu
70GB Ubuntu

---

### Post by mister_playboy on 2010-10-23
You should be able to install Debian to either the 70 or 73GiB partitions with no problem.

---

### Post by dcstar on 2010-10-23
> **DougieFresh4U said:**
> Most likely discussed ad nauseam.
Simple question (I hope), I have a triple boot system and would like to add Debian as well. I first installed Win7 then I let partitioner split hard drive when installing Ubuntu. When I installed my second Ubuntu, I let partitioner split the first Ubuntu space in half. When installing Debian, is the installer the same and will it set up another partition and add the entry to grub and not screw everything up (eat my grub menu:mad:)
320GB hard drive:
167GB-Win7
73GB Ubuntu
70GB Ubuntu

You will have to tell the Debian install **not** to install grub (or whatever bootloader it uses).

When the Debian install finishes, boot up Ubuntu and do this to add in the new OS to your list:

```
sudo update-grub
```

---

