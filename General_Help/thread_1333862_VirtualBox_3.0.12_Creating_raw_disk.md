---
title: "VirtualBox 3.0.12 Creating raw disk"
date: 2009-11-21
forum: General Help
---

### Post by ibates on 2009-11-21
Creating raw disk - Access denied dialogue

(This post appears on VirtualBox forum as well).

Ubuntu 9.10 on one HDD. Win XP SP3 on another independent HDD.

Ubuntu 9.10 is the Host and it is my intention to make Win XP the Guest in a VirtualBox VM.

Attempts to install "Access to entire physical hard disk" as per VirtualBox User Manual 9.10.1 with

"VBoxManage internalcommands createrawvmdk -filename /home/XYZ/WinXPHDD.vmdk -rawdisk /dev/sdc -register"
(XYZ is user name)

fail each attempt with the dialogue:

"Error opening the raw disk '/dev/sdc': VERR_ACCESS_DENIED
The raw disk vmdk file was not created"

The drive specification /dev/sdc is correct.

I have administrator privileges in both Win XP (one boot option), and in Ubuntu 9.10 (another boot option.

How can I overcome this problem? I cannot think of a solution.

---

