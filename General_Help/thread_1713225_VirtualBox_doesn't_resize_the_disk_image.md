---
title: "VirtualBox doesn't resize the disk image"
date: 2011-03-23
forum: General Help
---

### Post by rva1945 on 2011-03-23
When I created the disk, I specified dynamically growth, but when I tried to copy a file larger than the available disk space (500MB), a message showed up saying that it couldn't be done.

According to VirtualBox help, Image resizing was added with VirtualBox 4.0:

VBoxManage modifyhd
<uuid>|<filename>
[--type normal|writethrough|immutable|shareable|
readonly|multiattach]
[--autoreset on|off]
[--compact]
[--resize <megabytes>|--resizebyte <bytes>]

So why my VirtualBox 3.2.8 let me create the disk with dynamically growth option??

---

### Post by anglican on 2011-03-24
> **rva1945 said:**
> When I created the disk, I specified dynamically growth, but when I tried to copy a file larger than the available disk space (500MB), a message showed up saying that it couldn't be done.

According to VirtualBox help, Image resizing was added with VirtualBox 4.0:

VBoxManage modifyhd
<uuid>|<filename>
[--type normal|writethrough|immutable|shareable|
readonly|multiattach]
[--autoreset on|off]
[--compact]
[--resize <megabytes>|--resizebyte <bytes>]

So why my VirtualBox 3.2.8 let me create the disk with dynamically growth option??I think you might be confusing two different things here. When you create a dynamically resizing disk image it means that the disk image file will grow as you add content to the image up to the limit of the size you created. i.e. if there's only 400MB space left you can't add 500MB to the disk. But... you can then use VBoxManage to increase the size of the virtual disk, remembering that your partitions on that bigger disk will not automatically get the extra new space. You will need to run something like gparted (in the VM - you can boot from an iso if your VM can't run it) to resize the the partition to use the extra space you've added with "VBoxManage modifyhd --resize".

H

---

### Post by rva1945 on 2011-03-24
> **anglican said:**
> I think you might be confusing two different things here. When you create a dynamically resizing disk image it means that the disk image file will grow as you add content to the image up to the limit of the size you created. i.e. if there's only 400MB space left you can't add 500MB to the disk. But... you can then use VBoxManage to increase the size of the virtual disk, remembering that your partitions on that bigger disk will not automatically get the extra new space. You will need to run something like gparted (in the VM - you can boot from an iso if your VM can't run it) to resize the the partition to use the extra space you've added with "VBoxManage modifyhd --resize".

H

OK, now where I download that iso to? Because there's no more available room in the VM. Could it be the shared folder (accessed via guest additions)?

---

### Post by anglican on 2011-03-28
> **rva1945 said:**
> OK, now where I download that iso to? Because there's no more available room in the VM. Could it be the shared folder (accessed via guest additions)?Download it in the host and then select it as your CD iso for the VM. Then boot the VM from the CD.

H

---

### Post by timgood on 2011-03-28
You have already asked this question and it already has been replied to, several times.

[http://ubuntuforums.org/showthread.php?t=1713305](http://ubuntuforums.org/showthread.php?t=1713305)

Hope this helps.

---

