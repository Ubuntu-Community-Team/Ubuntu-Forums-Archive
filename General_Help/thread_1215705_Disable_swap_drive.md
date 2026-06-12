---
title: "Disable swap drive"
date: 2009-07-17
forum: General Help
---

### Post by GBLinux on 2009-07-17
Hi,

I want to know how do i disable swap drive in linux.

syntax: sudo swapoff

I know it shows some prefixes which I'm not aware of, can you tell exact syntax. 

Thank You!

---

### Post by ddrichardson on 2009-07-17
```
sudo swapoff /dev/partition
```Where partition is the swap partition.

This will still be mounted at boot unless you comment it out from /etc/fstab

---

### Post by GBLinux on 2009-07-18
> **ddrichardson said:**
> ```
sudo swapoff /dev/partition
```Where partition is the swap partition.

This will still be mounted at boot unless you comment it out from /etc/fstab

I don't know the partition path of my swap drive please tell me the method to list the partition.

---

### Post by Rocket2DMn on 2009-07-18
Can you please post the output of
```
sudo fdisk -l
```
That will show us your partitions, and we can help you identify your swap.  You may even be able to see it yourself :)

---

### Post by CREEPING DEATH on 2009-07-18
```
sudo swapoff -a
```
The -a turns all swap partitions off.

CD

---

### Post by GBLinux on 2009-07-18
> **CREEPING DEATH said:**
> ```
sudo swapoff -a
```The -a turns all swap partitions off.

CD

Thank you i have located the swap drive and have disabled it.

---

### Post by fragos on 2009-07-18
Disabling swap may cause you problems. I assume you wanted to improve performance. I recommend you add more RAM until you don't normally need swap. 1GB did it for me. You can change swappiness control by doing the following:

sudo gedit /etc/sysctl.conf

Find the line containing "vm.swappiness=" and change the number to the one you'd like to try.  In my case "vm.swappiness=10". Run "sudo sysctl -p" to make the change now or it will happen with the next boot.

---

### Post by schilcha on 2009-07-18
just forget it

---

