---
title: "How to control fan speed on 11.04"
date: 2011-05-22
forum: General Help
---

### Post by 381hfk328fn38d1 on 2011-05-22
.

---

### Post by Hedgehog1 on 2011-05-22
This works on many (but not all) laptops to keep the CPU cool and the fans from being too noisy:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by xMohd on 2011-05-27
Hello, I've been looking every where for a solution, tried several, no use. I use a workstation. when booting Windows it's super quiet, only gets noisy if it heats up. When booting ubuntu 11.04, we have to fasten the seat belts coz it looks like we're about to take off :) I tried your solution & it does not work unfortunately. Wish we can get more input in this post.

---

### Post by Telephonez_me on 2011-09-08
@[Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016")
Thanks for that. My laptop is silent since I had the line, can even sleep at night.

---

### Post by .... on 2011-09-08
For non-laptops, you use pwmconfig and fancontrol (you might need to install lm-sensors package).

---

