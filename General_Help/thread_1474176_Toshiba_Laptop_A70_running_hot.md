---
title: "Toshiba Laptop A70 running hot"
date: 2010-05-05
forum: General Help
---

### Post by bj44 on 2010-05-05
I have a Toshiba Satellite A70 running 10.04. It runs really hot, with a CPU temp of nearly 85 C.
 
I do think it is related to 10.04 installation since I do not have any fan issues running Windows nor did have any with previous versions of Ubuntu.
 
I have updated the /etc/defaults/grub file to slow down the never _stopping_ fan on my Laptop based on what I have read in Forums. Here is a copy of updated grub file (partial) in Lucia.
 
 ...................................................
 
#  /etc/defaults/grub
 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\""
[COLOR=Blue]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=Linux"[/COLOR]
# GRUB_CMDLINE_LINUX=""
# GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"
.....................................................
 
 
 
Is there a possibility to control the fan permanently?
 
 
Thank you

---

### Post by mexlinux on 2010-05-10
Join this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156)

---

