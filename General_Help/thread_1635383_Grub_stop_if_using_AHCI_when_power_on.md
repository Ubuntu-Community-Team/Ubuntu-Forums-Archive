---
title: "Grub stop if using AHCI when power on"
date: 2010-12-01
forum: General Help
---

### Post by cariocap on 2010-12-01
Hi all,

If I change my sata mode from IDE to AHCI grub won't show (cursor goes to top left) when I power on my system. After that, I press the reset button and my grub shows ok.

So, to use AHCI I always have to use the reset switch button.

Using Ubuntu 10.10 with 2.6.35-23-generic - 64bits

Anyone know how to fix it ? 

Thanks in advance

---

### Post by cariocap on 2010-12-08
bump

---

### Post by dcstar on 2010-12-08
> **cariocap said:**
> Hi all,

If I change my sata mode from IDE to AHCI grub won't show (cursor goes to top left) when I power on my system. After that, I press the reset button and my grub shows ok.

So, to use AHCI I always have to use the reset switch button.

Using Ubuntu 10.10 with 2.6.35-23-generic - 64bits

Anyone know how to fix it ? 

Thanks in advance

Set your BIOS to have a Hard Drive delay, this seems to be an issue in your hardware.

---

### Post by cariocap on 2010-12-09
Hi,

Thanks for your help.

Unfortunately I can't find any hard drive delay option in my ECS A780GM-A V1.1 motherboard BIOS.

Maybe this delay can be set at grub.

---

### Post by cariocap on 2010-12-09
Solved.

In /etc/default/grub I uncommented the line:
#GRUB_DISABLE_LINUX_UUID=true

So the steps are:

sudo gedit /etc/default/grub
uncomment the line #GRUB_DISABLE_LINUX_UUID=true, removing the # and saving the file
sudo update-grub

---

### Post by cariocap on 2010-12-11
the problem still occurs

---

