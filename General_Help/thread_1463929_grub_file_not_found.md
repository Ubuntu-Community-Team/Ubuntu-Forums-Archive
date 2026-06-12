---
title: "grub file not found"
date: 2010-04-27
forum: General Help
---

### Post by rahulponna on 2010-04-27
Hi,

 I already had ubuntu 32 bit version 9.10. but due to some tool compatibility reason I need even the 64 bit version 9.10. I dint want to delete 32 bit version so I wanted to install both on my system. I have windows vista as well.
 So I booted with 64 bit version of Ubuntu, went on with the installation, until the point were it asks to choose the partition. 32 bit version had 16GB allocated and 10GB free. so I thought I will make new 8GB partition from the 10GB free space. So I selected the partition and clicked on change, and specified 8GB and ext4 format and mount point as "/". I clicked on continue and in a few seconds it popped up with an ERROR message, which I can't remember exactly, but it meant to say that it could not make the changes as the disk to which the changes were made is in use. So I should not use it until I reboot. So I rebooted and now I have grub error : file not found and grub rescue> prompt.
I tried to boot with the 64 bit CD again with the option of trying ubuntu without making any changes and it does show the 16 GB partition, but when I mount that partition I do not see any folders in the partition except for a folder named "lost+found". I try to view the contents of this and it says I do not have the permissions.
Hope I could make you understand my problem. Can any body help?

---

### Post by rahulponna on 2010-04-27
I did also run the boot_info_script055.sh file which I found on ubuntu forum itself.

This RESULT file the script generated is attached. I do not have the option of booting from USB drive. Is there a way to restore the grub loader ?

---

### Post by rahulponna on 2010-04-27
I managed to find the error which I have mentioned before.

"Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting."

ERROR !!

Somebody please help..

---

### Post by oldos2er on 2010-04-27
> **rahulponna said:**
>  So I booted with 64 bit version of Ubuntu, went on with the installation, until the point were it asks to choose the partition. 32 bit version had 16GB allocated and 10GB free. so I thought I will make new 8GB partition from the 10GB free space. So I selected the partition and clicked on change, and specified 8GB and ext4 format and mount point as "/". I clicked on continue and in a few seconds it popped up with an ERROR message, which I can't remember exactly, but it meant to say that it could not make the changes as the disk to which the changes were made is in use. 

It sounds like you attempted to install while some of your hard disk partitions were mounted. I would try reinstalling, but first make sure none of your partitions are mounted.

---

