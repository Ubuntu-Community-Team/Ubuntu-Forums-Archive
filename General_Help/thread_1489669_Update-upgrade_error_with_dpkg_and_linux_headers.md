---
title: "Update-upgrade error with dpkg and linux headers"
date: 2010-05-21
forum: General Help
---

### Post by petaloid on 2010-05-21
I don't fully understand what happened, but recently I had to do a reinstallation of ubuntu.

Whenever I run,
```
sudo apt-get update
sudo apt-get upgrade
```

I get the following output,
```
generho@veda:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils libpangomm-1.4-1 software-center
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 2,474kB of archives.
After this operation, 8,192B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main apt 0.7.25.3ubuntu9 [1,818kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main apt-utils 0.7.25.3ubuntu9 [238kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main apt-transport-https 0.7.25.3ubuntu9 [80.9kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libpangomm-1.4-1 2.26.2-0ubuntu1 [58.8kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main software-center 2.0.4 [278kB]
Fetched 2,474kB in 2s (829kB/s)    
(Reading database ... 141979 files and directories currently installed.)
Preparing to replace apt 0.7.25.3ubuntu8 (using .../apt_0.7.25.3ubuntu9_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.7.25.3ubuntu9) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 141979 files and directories currently installed.)
Preparing to replace apt-utils 0.7.25.3ubuntu8 (using .../apt-utils_0.7.25.3ubuntu9_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace apt-transport-https 0.7.25.3ubuntu8 (using .../apt-transport-https_0.7.25.3ubuntu9_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace libpangomm-1.4-1 2.26.1-1 (using .../libpangomm-1.4-1_2.26.2-0ubuntu1_amd64.deb) ...
Unpacking replacement libpangomm-1.4-1 ...
Preparing to replace software-center 2.0.3 (using .../software-center_2.0.4_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
[B]Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-22-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-22-generic (2.6.32-22.33) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-22-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-22-generic; however:
  Package linux-headers-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up apt-utils (0.7.25.3ubuntu9) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already

Setting up apt-transport-https (0.7.25.3ubuntu9) ...
Setting up libpangomm-1.4-1 (2.26.2-0ubuntu1) ...

Setting up software-center (2.0.4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-22-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

```
Irrespective of whatever comes before, the bold part always shows up.

I'm fairly used to using linux, and I can follow any instructions to get information that you may need to help me with this strange problem so ask away.

---

### Post by petaloid on 2010-05-21
> I tried doing what was in this thread: [http://ubuntuforums.org/showthread.php?t=986113](http://ubuntuforums.org/showthread.php?t=986113)
No luck.

> Also [http://ubuntuforums.org/archive/index.php/t-541998.html](http://ubuntuforums.org/archive/index.php/t-541998.html)
Did not help

-petaloid

---

### Post by bapoumba on 2010-05-21
This is a know bug with the nvidia-common package (will edit this post to give you the bug link).
Do you have anything nvidia ? If not, try removing the package and proceed with the update/upgrade.

---

### Post by bapoumba on 2010-05-21
Sorry to bump with a new post, as I found the bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

Removing is not enough, please try:
```
sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common
```

---

### Post by petaloid on 2010-05-21
Yes I have an nvidia card. I did notice a problem trying to activate the proprietary drivers.

Once I started the purge process it immediately went into the same depmod process as before, but this time it completed successfully.

Now the error is gone thank you!

---

### Post by bapoumba on 2010-05-21
Glad to see you got it sorted out :)

---

### Post by ToniMe on 2010-06-08
> **bapoumba said:**
> Sorry to bump with a new post, as I found the bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

Removing is not enough, please try:
```
sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common
```

I confirm. Reinstalling nvidia-common fixes the problem. Many thanks Bapoumba!

---

### Post by Kalit101 on 2010-06-24
> **ToniMe said:**
> I confirm. Reinstalling nvidia-common fixes the problem. Many thanks Bapoumba!

I had the same initial error message as the petaloid, it was also after I had reinstalled Linux on my system.  My graphics card is a NVIDIA and I tried the code provided by **bapoumba** and was able to un-install the nvidia-common but am getting the following when reinstalling it:


rbrown@RBrown-DELL:~$ sudo apt-get install nvidia-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 13.9kB of archives.
After this operation, 184kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main nvidia-common 0.2.23 [13.9kB]
Fetched 13.9kB in 0s (22.9kB/s)      
Preconfiguring packages ...
Selecting previously deselected package nvidia-common.
(Reading database ... 151721 files and directories currently installed.)
Unpacking nvidia-common (from .../nvidia-common_0.2.23_amd64.deb) ...
Setting up linux-headers-2.6.32-22-generic (2.6.32-22.36) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-22-generic; however:
  Package linux-headers-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-common (0.2.23) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Processing triggers for python-central ...
Errors were encountered while processing:
 linux-headers-2.6.32-22-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Sorry I don't know how to box the error report like the petaloid, I am very new at Linux as well as using forums. If anyone can help me with this, and maybe tell me how to put a scroll box within my reply,  I would be much appreciative. :)  Also for my windows key does not seem to be working after the re-install for my keyboard shortcuts, is this because of the linux-header being missing or another issue I need to fix?

---

### Post by cherry316316 on 2010-11-09
> **bapoumba said:**
> Sorry to bump with a new post, as I found the bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

Removing is not enough, please try:
```
sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common
```

this works. 
damm the nivida beta driver.

thanks a lot.

---

### Post by vidasov on 2011-01-28
Is this error only related to nvidia? 
This is my output:

```

$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.32-28 linux-headers-2.6.32-28-generic-pae linux-image-2.6.32-28-generic-pae
The following packages will be upgraded:
  apparmor apparmor-utils at bsdutils dpkg fuse-utils ifupdown libapache2-mod-php5 libapparmor-perl libapparmor1 libblkid1 libc-bin libc6 libc6-i686
  libdbus-1-3 libfuse2 libmysqlclient16 libplymouth2 libuuid1 linux-firmware linux-generic-pae linux-headers-generic-pae linux-image-generic-pae mount
  mysql-client-5.1 mysql-client-core-5.1 mysql-common mysql-server mysql-server-5.1 mysql-server-core-5.1 openssh-client openssh-server php5-common
  php5-mysql plymouth plymouth-theme-ubuntu-text sudo util-linux uuid-runtime
39 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 77.5MB/89.6MB of archives.
After this operation, 186MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mount 2.17.2-0ubuntu1.10.04.2 [175kB]
Get:2 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main util-linux 2.17.2-0ubuntu1.10.04.2 [533kB]
Get:3 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main bsdutils 1:2.17.2-0ubuntu1.10.04.2 [81.2kB]
Get:4 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-28-generic-pae 2.6.32-28.55 [31.6MB]
Get:5 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.41-3ubuntu12.9 [98.8kB]                                                      
Get:6 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server 5.1.41-3ubuntu12.9 [94.8kB]                                                      
Get:7 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.41-3ubuntu12.9 [1,933kB]                                                 
Get:8 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-client-core-5.1 5.1.41-3ubuntu12.9 [178kB]                                              
Get:9 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-client-5.1 5.1.41-3ubuntu12.9 [8,140kB]                                                 
Get:10 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server-core-5.1 5.1.41-3ubuntu12.9 [4,714kB]                                           
Get:11 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server-5.1 5.1.41-3ubuntu12.9 [7,009kB]                                                
Get:12 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main libuuid1 2.17.2-0ubuntu1.10.04.2 [61.8kB]                                                    
Get:13 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main libblkid1 2.17.2-0ubuntu1.10.04.2 [111kB]                                                    
Get:14 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth 0.8.2-2ubuntu2.2 [115kB]                                                            
Get:15 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main libplymouth2 0.8.2-2ubuntu2.2 [92.0kB]                                                       
Get:16 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main apparmor 2.5.1-0ubuntu0.10.04.3 [354kB]                                                      
Get:17 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main libapparmor1 2.5.1-0ubuntu0.10.04.3 [41.5kB]                                                 
Get:18 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main libapparmor-perl 2.5.1-0ubuntu0.10.04.3 [43.1kB]                                             
Get:19 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main apparmor-utils 2.5.1-0ubuntu0.10.04.3 [108kB]                                                
Get:20 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main at 3.1.11-1ubuntu5.1 [47.0kB]                                                                
Get:21 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-server 1:5.3p1-3ubuntu5 [285kB]                                                      
Get:22 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-client 1:5.3p1-3ubuntu5 [761kB]                                                      
Get:23 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-text 0.8.2-2ubuntu2.2 [20.6kB]                                         
Get:24 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main uuid-runtime 2.17.2-0ubuntu1.10.04.2 [63.9kB]                                                
Get:25 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-firmware 1.34.3 [10.2MB]                                                               
Get:26 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-generic-pae 2.6.32.28.31 [4,312B]                                                      
Get:27 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-generic-pae 2.6.32.28.31 [4,320B]                                                
Get:28 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-28 2.6.32-28.55 [9,907kB]                                               
Get:29 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-28-generic-pae 2.6.32-28.55 [766kB]                                     
Get:30 http://hr.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-generic-pae 2.6.32.28.31 [4,308B]                                              
Fetched 77.5MB in 30s (2,520kB/s)                                                                                                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 79717 files and directories currently installed.)
Preparing to replace dpkg 1.15.5.6ubuntu4.4 (using .../dpkg_1.15.5.6ubuntu4.5_i386.deb) ...
**Unpacking replacement dpkg ...**


```
and wait on that point
This is my uname: 

```

$ uname -a
Linux buntuSRV 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
$ 

```

---

### Post by dustman on 2011-06-29
> **bapoumba said:**
> Sorry to bump with a new post, as I found the bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

Removing is not enough, please try:
```
sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common
```


I confirm it too...works great!

---

