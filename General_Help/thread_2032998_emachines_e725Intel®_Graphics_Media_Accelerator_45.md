---
title: "emachines e725/Intel® Graphics Media Accelerator 4500M help needed"
date: 2012-07-25
forum: General Help
---

### Post by Sarys on 2012-07-25
So I'm using Ubuntu 12.04 but that dosen't support my "video card"? So my backlight dosen't work. But I fixed it by editing /etc/rc.local. I added line /usr/bin/setpci -s 00:02.0 F4.B=80 above 0 line. So it fixed the problem but I can't change brightness.
But now I have new problem. I installed playonlinux and Civilization 4 Colonization. Everything went fine but when I tried to launche the game my backlight tunrs off so I can't play windows games. So if someone know how to fix this please let me know.

EDIT: I know I could use 10.04 because that works without problem I just want this problem to be fixed so I can use never versions as well.
           Or then I could try different Linux version (distro?) but I want to stick in Ubuntu if possible.

EDIT2: Problem solved I just needed to use virtual desktop.

---

### Post by Sarys on 2012-07-25
Okay the virtual desktop works. But I'd still want to get this thing fixed if possible.

---

### Post by williejones on 2012-07-25
I have the emachines e725 and had the same issue. I solved mine by the following:

1.  Add to kernel boot parameters: acpi_backlight=vendor i915.invert_brightness=1

2.  You can make them permanent by editing /etc/default/grub , editing this line:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i915.invert_brightness=1"
 then run:
 update-grub2

---

### Post by Sarys on 2012-07-26
> **williejones said:**
> I have the emachines e725 and had the same issue. I solved mine by the following:

1.  Add to kernel boot parameters: acpi_backlight=vendor i915.invert_brightness=1

2.  You can make them permanent by editing /etc/default/grub , editing this line:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i915.invert_brightness=1"
 then run:
 update-grub2

Thanks that fixed my problem :)

---

