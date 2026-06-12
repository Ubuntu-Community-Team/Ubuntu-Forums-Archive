---
title: "Ubuntu 9.10 shutdown problem"
date: 2010-04-05
forum: General Help
---

### Post by GSMS on 2010-04-05
I installed Ubuntu 9.10 Alternate on a Pentium III pc. (256MB RAM, 40GB Hard Disk) It works fine but the shutdown never fully completes. I left the computer for a couple of hours after commanding shutdown but it still doesn't shutdown. All I get is a message (picture in attachment). 

Is there a solution for this problem?

---

### Post by NightwishFan on 2010-04-05
I am unsure of a solution, however it seems Linux does not know how to turn your machine off via ACPI. Perhaps report this as a bug, but I would like to ask does Windows have this same behavior? If so then it is expected and might just be a hardware limitation.

In any case, when the system is like that, it is safe to power it off manually. (By holding in the power button?)

---

### Post by GSMS on 2010-04-05
> **NightwishFan said:**
> I am unsure of a solution, however it seems Linux does not know how to turn your machine off via ACPI. Perhaps report this as a bug, but I would like to ask does Windows have this same behavior? If so then it is expected and might just be a hardware limitation.

In any case, when the system is like that, it is safe to power it off manually. (By holding in the power button?)
Windows XP on the computer shutdowns without problems. By the way, what is ACPI?

---

### Post by NightwishFan on 2010-04-05
What Linux uses to talk to the computers power management I think. ;)

Try This:
[LIST=1]
[*]Press E to edit the Ubuntu kernel when got get to the boot menu. You will see a bunch of lines.
[*]Scroll down to one that starts with "Linux" or "Kernel" (not sure which of the top of my head. Hit the end key to go to the end of the line.
[*]Add a space and type this: ```
acpi=force
```
[*]Press ctrl+x to boot, then tell the computer to shut down. Does it work?
[*]If so please report it here so we can make the change permanent. Right now it will only work for this one boot.
[/LIST]

Any questions?

---

### Post by GSMS on 2010-04-05
> **NightwishFan said:**
> What Linux uses to talk to the computers power management I think. ;)

Try This:
[LIST=1]
[*]Press E to edit the Ubuntu kernel when got get to the boot menu. You will see a bunch of lines.
[*]Scroll down to one that starts with "Linux" or "Kernel" (not sure which of the top of my head. Hit the end key to go to the end of the line.
[*]Add a space and type this: ```
acpi=force
```
[*]Press ctrl+x to boot, then tell the computer to shut down. Does it work?
[*]If so please report it here so we can make the change permanent. Right now it will only work for this one boot.
[/LIST]

Any questions?
That worked. :D

---

### Post by NightwishFan on 2010-04-05
Excellent, I am glad it works. Here is how to make it permanent.

[LIST=1]
[*]Press alt+f2 and type: ```
gksudo gedit /etc/default/grub
```
[*]Find the line that looks like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" Change it to: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
```
[*]Open Applications -> Accessories -> Terminal and run this command, you will need to type your password but it will not show up. ```
sudo update-grub
```
[*]When you reboot it will take effect.
[/LIST][LIST=1]
[/LIST]

---

### Post by GSMS on 2010-04-06
> **NightwishFan said:**
> Excellent, I am glad it works. Here is how to make it permanent.

[LIST=1]
[*]Press alt+f2 and type: ```
gksudo gedit /etc/default/grub
```
[*]Find the line that looks like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" Change it to: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
```
[*]Open Applications -> Accessories -> Terminal and run this command, you will need to type your password but it will not show up. ```
sudo update-grub
```
[*]When you reboot it will take effect.
[/LIST][LIST=1]
[/LIST]
Thanks. :D By the way, how do I delete the old versions selected in bold:
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
[b]Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic[/b]
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1

---

### Post by NightwishFan on 2010-04-06
From a terminal:
```
sudo aptitude purge linux-image-2.6.31-14-generic
```

---

### Post by GSMS on 2010-04-06
> **NightwishFan said:**
> From a terminal:
```
sudo aptitude purge linux-image-2.6.31-14-generic
```

Thanks. :D 

My last question: How do we change the default screen resolution in ubuntu? (login screen, user resolution, etc.)

---

