---
title: "reading ext4 from ext3"
date: 2009-11-03
forum: General Help
---

### Post by mosaic2s on 2009-11-03
How do I read disk formatted as ext4 under 9.10 from 8.04 LTS?

---

### Post by cariboo on 2009-11-03
You should be able to see it just like any other type of partition. I access ext4 partitions remotely, using either samba or nfs either utility does the translation so the partition type is irrelevant.

---

### Post by mosaic2s on 2009-11-03
I tried reading the partition. It said that the partition is formatted as ext4 and can not be read.
This was thru 8.04LTS.

Also, ext2 IFS is unable to read the linux partitions after being formatted for 9.10. Any advice?

---

### Post by ubfu on 2010-10-12
I have the same problem , I had hardy 8.04 installed but I can't read or mount ext4 (Lucid)
"Partition is formatted as ext4 and can not be read"

Anyone know how to enable ext3 hardy to read or mount ext4 ?

---

### Post by rusty149 on 2010-10-12
The best way is to upgrade the hardy kernel for ext4 support. I have tested this on a clean install (after standard updates) of Ubuntu 8.04 (ext3 32-bit) dual-booting Xubuntu 10.10 (ext4 32-bit).    Upgrade Kernel to version 2.6.28. Architecture: i386 (32-bit) 

```
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-headers-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-image-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-headers-2.6.28-020628_2.6.28-020628_all.deb
sudo wget http://gr.archive.ubuntu.com/ubuntu/pool/main/f/findutils/findutils_4.4.0-2ubuntu4_i386.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu6.2_i386.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.9-4ubuntu6.2_i386.deb
sudo dpkg -i ./libc6_2.9-4ubuntu6.2_i386.deb ./findutils_4.4.0-2ubuntu4_i386.deb
sudo dpkg -i ./libc6-i686_2.9-4ubuntu6.2_i386.deb
sudo dpkg -i ./linux-headers-2.6.28-020628_2.6.28-020628_all.deb
sudo dpkg -i ./linux-headers-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo dpkg -i ./linux-image-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo rm ./linux-image-2.6.28-020628-generic_2.6.28-020628_i386.deb ./linux-headers-2.6.28-020628* ./libc6-i686_2.9-4ubuntu6.2_i386.deb ./libc6_2.9-4ubuntu6.2_i386.deb ./findutils_4.4.0-2ubuntu4_i386.deb

sudo apt-get update && sudo apt-get dist-upgrade  
```Make sure the dist-upgrade does not produce any errors, such as 'unmet dependencies'. Then reboot system and test using mount.   

If hardy (8.04) was installed last then the GRUB boot loader will be legacy version 1 and will not recognize ext4 OS. Here is all you need to know about GRUB2  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  

Let me know any of problems you encounter.

Edit: This does not format the partitions. It adds support to mount ext4 drives. Hardy partition will still be ext3.

---

### Post by rusty149 on 2010-10-23
Here is the version for amd64 architecture (64-bit). 
This has now been tested (thanks to Kwill)

```

sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-headers-2.6.28-020628-generic_2.6.28-020628_amd64.deb
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-image-2.6.28-020628-generic_2.6.28-020628_amd64.deb
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-headers-2.6.28-020628_2.6.28-020628_all.deb
sudo wget http://gr.archive.ubuntu.com/ubuntu/pool/main/f/findutils/findutils_4.4.0-2ubuntu4_amd64.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu6.3_amd64.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.9-4ubuntu6.3_amd64.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.9-4ubuntu6.3_amd64.deb
sudo dpkg -i ./libc6_2.9-4ubuntu6.3_amd64.deb ./findutils_4.4.0-2ubuntu4_amd64.deb
sudo dpkg -i ./libc6-i386_2.9-4ubuntu6.3_amd64.deb
sudo dpkg -i ./libc6-dev_2.9-4ubuntu6.3_amd64.deb
sudo dpkg -i ./linux-headers-2.6.28-020628_2.6.28-020628_all.deb
sudo dpkg -i ./linux-headers-2.6.28-020628-generic_2.6.28-020628_amd64.deb
sudo dpkg -i ./linux-image-2.6.28-020628-generic_2.6.28-020628_amd64.deb
sudo rm ./linux-image-2.6.28-020628-generic_2.6.28-020628_amd64.deb ./linux-headers-2.6.28-020628* ./libc6-i386_2.9-4ubuntu6.3_amd64.deb ./libc6_2.9-4ubuntu6.3_amd64.deb ././libc6-dev_2.9-4ubuntu6.3_amd64.deb ./findutils_4.4.0-2ubuntu4_amd64.deb

sudo apt-get update && sudo apt-get dist-upgrade
```

Make sure the dist-upgrade does not produce any errors, such as 'unmet dependencies'. Then reboot system and test using mount. 

Enjoy

---

### Post by 3Miro on 2010-10-23
ext4 support was first introduced in 9.04 as an experimental feature. Older kernels cannot read ext4. If you are trying to access that via a network like cariboo907 suggests, then it really doesn't matter. However, if you are talking about a different partition on the same machine (as in dual-boot), then rusty149's solution is your best bet.

---

### Post by kwill on 2010-10-27
I tried the 64bit update and found it also needed to update libc6-dev so I added the following after the lines with libc6-i386 in


sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.9-4ubuntu6.3_amd64.deb


sudo dpkg -i ./libc6-dev_2.9-4ubuntu6.3_amd64.deb

In my case for some unkown reason it didn't output a initrd.img  so I had to reinstall kernel.  That meant down loading it again (22M). So it might be a good thing to not do the:

sudo rm ./linux-image-2.6.28-020628-generic_2.6.28-020628_amd64.deb ./linux-headers-2.6.28-020628* ./libc6-i386_2.9-4ubuntu6.3_amd64.deb ./libc6_2.9-4ubuntu6.3_amd64.deb ./findutils_4.4.0-2ubuntu4_amd64.deb

line until you have checked.

Once I booted the new kernel, updated fstab to take the ext4 partion, issued mount command and there it was.

Many thanks to Rusty149

---

### Post by kwill on 2010-10-27
Sorry Rusty149,

Didn't look close enough to see you had updated your script until I had posted.  If I had I would not have posted the changes.

---

### Post by kwill on 2011-05-13
The file versions of some of the files have changed.  You will need to look in:

[http://security.ubuntu.com/ubuntu/dists/](http://security.ubuntu.com/ubuntu/dists/)

To find the most recent version number.

---

### Post by atulrunthala on 2012-12-09
Thank You rusty149

It is working for me...

---

### Post by atulrunthala on 2012-12-09
> **rusty149 said:**
> The best way is to upgrade the hardy kernel for ext4 support. I have tested this on a clean install (after standard updates) of Ubuntu 8.04 (ext3 32-bit) dual-booting Xubuntu 10.10 (ext4 32-bit).    Upgrade Kernel to version 2.6.28. Architecture: i386 (32-bit) 

```
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-headers-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-image-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.28/linux-headers-2.6.28-020628_2.6.28-020628_all.deb
sudo wget http://gr.archive.ubuntu.com/ubuntu/pool/main/f/findutils/findutils_4.4.0-2ubuntu4_i386.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu6.2_i386.deb
sudo wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.9-4ubuntu6.2_i386.deb
sudo dpkg -i ./libc6_2.9-4ubuntu6.2_i386.deb ./findutils_4.4.0-2ubuntu4_i386.deb
sudo dpkg -i ./libc6-i686_2.9-4ubuntu6.2_i386.deb
sudo dpkg -i ./linux-headers-2.6.28-020628_2.6.28-020628_all.deb
sudo dpkg -i ./linux-headers-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo dpkg -i ./linux-image-2.6.28-020628-generic_2.6.28-020628_i386.deb
sudo rm ./linux-image-2.6.28-020628-generic_2.6.28-020628_i386.deb ./linux-headers-2.6.28-020628* ./libc6-i686_2.9-4ubuntu6.2_i386.deb ./libc6_2.9-4ubuntu6.2_i386.deb ./findutils_4.4.0-2ubuntu4_i386.deb

sudo apt-get update && sudo apt-get dist-upgrade  
```Make sure the dist-upgrade does not produce any errors, such as 'unmet dependencies'. Then reboot system and test using mount.   

If hardy (8.04) was installed last then the GRUB boot loader will be legacy version 1 and will not recognize ext4 OS. Here is all you need to know about GRUB2  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  

Let me know any of problems you encounter.

Edit: This does not format the partitions. It adds support to mount ext4 drives. Hardy partition will still be ext3.
Thank You ....It is working for me

---

### Post by oldfred on 2012-12-09
necromancy 
Closed, necromancy. Old thread closed.

From the Ubuntu Forums Code of Conduct.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

