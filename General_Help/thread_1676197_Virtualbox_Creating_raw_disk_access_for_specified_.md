---
title: "Virtualbox: Creating raw disk access for specified partitions"
date: 2011-01-26
forum: General Help
---

### Post by zweiundzwei on 2011-01-26
I want to be able to boot my Windows installation inside Ubuntu. After consulting the [Virtualbox Guide]("http://www.virtualbox.org/manual/ch09.html#rawdisk") I decided I want a vmdk file that only allows access to certain partitions (sda1 and sda3 in my case). 

As I understand, in my case the command is: 
```
sudo VBoxManage internalcommands createrawvmdk -filename /home/doro/virtualbox/xp.vmdk -rawdisk /dev/sda -partitions 1,3
```

I get this error: 
```
Oracle VM VirtualBox Command Line Management Interface Version 3.2.8_OSE
(C) 2005-2010 Oracle Corporation
All rights reserved.

ERROR: VMDK: could not create new file '/home/doro/virtualbox/xp.vmdk'
Error code VERR_FILE_NOT_FOUND at /build/buildd/virtualbox-ose-3.2.8-dfsg/src/VBox/Devices/Storage/VmdkHDDCore.cpp(3539) in function int vmdkCreateRawImage(VMDKIMAGE*, VBOXHDDRAW*, uint64_t)
Error while creating the raw disk VMDK: VERR_FILE_NOT_FOUND
The raw disk vmdk file was not created
```
I don't understand what this means or what I should do. Any ideas?

I use the version from the repositories. 

Thanks!

---

### Post by drewsus on 2011-01-26
```
sudo usermod -G disk,vboxusers -a `whoami`
```

**Log out/in**

```
sudo apt-get install mbr
install-mbr ~/.VirtualBox/FAKE.mbr -f
```

**Don't run with sudo:**
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/xp.vmdk -rawdisk /dev/sda -partitions 1,3 -mbr ~/.VirtualBox/FAKE.mbr -register -relative
```

Lifted from [HERE]("http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/"), modified for your needs.

dRewsus

---

