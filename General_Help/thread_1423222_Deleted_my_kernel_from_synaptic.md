---
title: "Deleted my kernel from synaptic"
date: 2010-03-06
forum: General Help
---

### Post by anderskitson on 2010-03-06
Hi I just installed ubuntu 9.10. I made a custom grub2 menu, but on boot I had multiple ubuntu kernels to choose from. I went into synaptic and deleted the wrong one. Do i have to go through the whole install process again. How can I restore the kernel. Thanks

---

### Post by 2hot6ft2 on 2010-03-06
> **anderskitson said:**
> Hi I just installed ubuntu 9.10. I made a custom grub2 menu, but on boot I had multiple ubuntu kernels to choose from. I went into synaptic and deleted the wrong one. Do i have to go through the whole install process again. How can I restore the kernel. Thanks
Yes you will have to reinstall that kernel if you want it. Just make sure you have at least 1 kernel before you reboot.

---

### Post by anderskitson on 2010-03-06
I am not sure how to go about doing this, I have the install disk. I get an error saying a kernel has to be loaded, that's why I posted this question because I can't get into ubuntu anymore for grub.

---

### Post by 2hot6ft2 on 2010-03-06
So you're saying you removed all of your kernels and rebooted.
I have no idea how to fix that short of reinstalling.
Might want to wait and see if anyone has another solution.

---

### Post by anderskitson on 2010-03-06
I only deleted one of the kernels, but the one that shows up in grub doesn't work. There were two to delete in synaptic, so I am not quite sure what the case is. I think I might just reinstall.

---

### Post by 2hot6ft2 on 2010-03-06
> **anderskitson said:**
> I only deleted one of the kernels, but the one that shows up in grub doesn't work. There were two to delete in synaptic, so I am not quite sure what the case is. I think I might just reinstall.
It might be faster to reinstall and I don't know of any way to fix it. So it's up to you.

---

### Post by sisco311 on 2010-03-06
> **anderskitson said:**
> I am not sure how to go about doing this, I have the install disk. I get an error saying a kernel has to be loaded, that's why I posted this question because I can't get into ubuntu anymore for grub.

[list=i]
[*]Boot a Live CD/USB, open a terminal and type:
```
sudo fdisk -l
```
The command should list your partitions. Find the device name of the root ("/") partition. i.e. /dev/sda1

[*]mount the partition:
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
```

[*]mount the virtual filesystems:
```
for i in dev dev/pts proc sys etc/resolv.conf; do sudo mount --bind /$i /mnt/ubuntu/$i; done
```

[*]chroot into ubuntu:
```
sudo chroot /mnt/ubuntu bash
```

[*]install the kernel:
```
apt-get install linux-image-2.6<press TAB to list the available kernel, pick the one you deleted>
```

[*]you may have to update grub:
```
update-grub
```

[*]exit from the chroot & reboot:
```
exit  #or press Ctrl+d
sudo reboot
```

[/list]

---

### Post by anderskitson on 2010-03-06
Thanks for the answer, I started to reinstall already. But I will most definitely keep this code for future issues. thanks Again

---

### Post by 2hot6ft2 on 2010-03-06
Nice instructions sisco311.
I'll have to save that info for future reference.

---

### Post by anderskitson on 2010-03-06
Maybe some one could help me or I will post a new question, but I have reinstalled now, and made a custom grub2 menu however both the default and the custom show together. So my grub looks like this, the bolded entries are my custom ones. How do I get rid of the others

ubuntu,linux ...
ubuntu,linux recovery
memtest
memtest
windows7
[B]windows7
ubuntu linux
ubuntu linux recover[/B]

---

### Post by sisco311 on 2010-03-06
> **anderskitson said:**
> Maybe some one could help me or I will post a new question, but I have reinstalled now, and made a custom grub2 menu however both the default and the custom show together. So my grub looks like this, the bolded entries are my custom ones. How do I get rid of the others

ubuntu,linux ...
ubuntu,linux recovery
memtest
memtest
windows7
[B]windows7
ubuntu linux
ubuntu linux recover[/B]

So, you  want windows to be the first menu entry then ubuntu.

EDIT: **backup the files first!**


rename 30_os-prober to 09_os-prober:
```
sudo mv /etc/grub.d/{30,09}_os-prober
```

and remove the execute permissions from 40_custom and 20_memtest86+
```
sudo chmod -x /etc/grub.d/{20_memtest86,40_custom}
```

then run:
```
sudo update-grub
```

---

### Post by anderskitson on 2010-03-06
I discovered my answer and added it to this thread. [http://ubuntuforums.org/showthread.php?p=8925999#post8925999](http://ubuntuforums.org/showthread.php?p=8925999#post8925999)

---

