---
title: "&quot;invalid or corrupt kernel image&quot; PXE Ubuntu 10.10"
date: 2010-12-29
forum: General Help
---

### Post by NFN_NLN on 2010-12-29
I have a PXE boot setup.  It is confirmed working as I can successfully boot other kernels (full SUSE10 distro).

However, when I dump the Ubuntu 10.10 kernel onto the PXE server, the client always reports the same error:

"invalid or corrupt kernel image"

This is with the basic "vmlinuz-2.6.35-24-generic-pae" file.

1) I've installed Ubuntu DIRECTLY on the system I was trying to boot from and it works fine (that's where I got the kernel from).

2) The file is NOT CORRUPT as I did an md5sum on the PXE server and the client and they have the same hash.

3) All files in the base /tftpboot directory with the same ownership/permissions.

<Original that works>

pxelinux.cfg/default:

prompt 0
default toolscenter
timeout 100
label toolscenter
display bsb.msg
kernel img2a
append initrd=img3a

<Fails with "invalid or corrupt kernel image">

pxelinux.cfg/default:

prompt 0
default toolscenter
timeout 100
label toolscenter
display bsb.msg
kernel vmlinuz-2.6.35-24-generic-pae
append initrd=initrd1

---

### Post by NFN_NLN on 2010-12-29
When it fails I'm left at a prompt where I can try to manually boot:

boot: random
Could not find kernel image: random
boot: vmlinuz-2.6.35-24-generic-pae
Loading
Invalid or corrupt kernel image.
boot:

---

### Post by dcstar on 2010-12-30
> **NFN_NLN said:**
> I have a PXE boot setup.  It is confirmed working as I can successfully boot other kernels (full SUSE10 distro).

However, when I dump the Ubuntu 10.10 kernel onto the PXE server, the client always reports the same error:

"invalid or corrupt kernel image"

This is with the basic "vmlinuz-2.6.35-24-generic-pae" file.
..........

There seems to be a lot more to booting Ubuntu via PXE than your setup:

[https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

---

### Post by NFN_NLN on 2010-12-30
When creating the initrd I missed this step:


Change the MODULES flag to netboot in /etc/initramfs-tools/initramfs.conf

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=netboot

---

