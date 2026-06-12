---
title: "Root partition disk space and /lib/modules"
date: 2011-03-27
forum: General Help
---

### Post by budojeepr on 2011-03-27
Hi all, I'm new to the forum but not all that new to Ubuntu nor Linux in other variants.

I have a disk space problem I'm hoping someone can help me with. I've researched the "recover lost disk space" threads which are loaded with good info but don't seem to be applicable.

I run an Ubuntu 10.04 server that is a virtual machine server (I cunningly called it "ark"). I have 3 KVM virtual servers running in it. All four of these servers are suffering the same problem, namely the root partition is filling up over time. These are servers - no X server, no desktop, no Trash, no nautilus.

It's a headless server, so I use SSH. Logging into ark, I'm greeted with:

```
System information as of Sun Mar 27 11:51:48 PDT 2011

  System load:    0.02              Processes:             159
  Usage of /home: 48.5% of 1.83GB   Users logged in:       0
  Memory usage:   59%               IP address for br0:    192.168.0.10
  Swap usage:     0%                IP address for virbr0: 192.168.122.1

  => / is using 85.4% of 460MB
```

When I set up each system, I partition carefully (of course the VMs don't have "/guest"):
[FONT="Courier New"]/dev/sda6                 461M  /
/dev/sda5                 92M   /boot
/dev/mapper/arkspace-tmp  4.6G  /tmp
/dev/mapper/arkspace-home 1.9G  /home
/dev/mapper/arkspace-var  4.6G  /var
/dev/mapper/arkspace-usr  9.2G  /usr
/dev/mapper/arkspace-guest 832G /guest[/FONT]

Previous reading indicated to me that 500MB is good for a / partition if you move other space hogs to their own partitions. guest is the partition where my virtual servers reside.

Every few days, I do an update/upgrade
```
# sudo apt-get update
# sudo apt-get upgrade
```

Now to the problem...

```
# df -h
Filesystem           	  Size  Used Avail Use% Mounted on
/dev/sda6             	  461M  394M   44M  91% /
none                  	  3.8G  280K  3.8G   1% /dev
none                  	  3.8G     0  3.8G   0% /dev/shm
none                  	  3.8G   84K  3.8G   1% /var/run
none                  	  3.8G     0  3.8G   0% /var/lock
none                 	  3.8G     0  3.8G   0% /lib/init/rw
/dev/mapper/arkspace-tmp  4.6G  138M  4.3G   4% /tmp
/dev/sda5              	  92M   56M   31M  65% /boot
/dev/mapper/arkspace-home 1.9G  908M  872M  52% /home
/dev/mapper/arkspace-var  4.6G  270M  4.1G   7% /var
/dev/mapper/arkspace-usr  9.2G  1.1G  7.7G  13% /usr
/dev/mapper/arkspace-guest 832G   38G  752G   5% /guest
```

Easy to see the root partition is bumping up against its limits.

Some wise person recommended this command to find big files:

```
# sudo find / -mount -ls | awk '{print $7, $11}' | sort -rn | less
```

The first few lines of its output:
```
1841392 /bin/busybox
1622304 /lib/libcrypto.so.0.9.8
1572232 /lib/libc-2.11.1.so
1388000 /lib/modules/2.6.32-27-server/kernel/fs/ocfs2/ocfs2.ko
1388000 /lib/modules/2.6.32-26-server/kernel/fs/ocfs2/ocfs2.ko
1383648 /lib/modules/2.6.32-24-server/kernel/fs/ocfs2/ocfs2.ko
1251036 /lib/firmware/i2400m-fw-usb-1.4.sbcf
1142480 /lib/firmware/i2400m-fw-usb-1.3.sbcf
1138424 /lib/modules/2.6.32-27-server/kernel/drivers/gpu/drm/radeon/radeon.ko
1138424 /lib/modules/2.6.32-26-server/kernel/drivers/gpu/drm/radeon/radeon.ko
1135184 /lib/modules/2.6.32-24-server/kernel/drivers/gpu/drm/radeon/radeon.ko
1121544 /lib/modules/2.6.32-27-server/kernel/drivers/staging/rt3090/rt3090sta.ko
1121544 /lib/modules/2.6.32-26-server/kernel/drivers/staging/rt3090/rt3090sta.ko
1121544 /lib/modules/2.6.32-24-server/kernel/drivers/staging/rt3090/rt3090sta.ko
1063520 /lib/libslang.so.2.2.2

# ls -l /lib/modules
drwxr-xr-x 4 root root 1024 2010-09-18 06:49 2.6.32-24-server
drwxr-xr-x 4 root root 1024 2010-11-30 06:27 2.6.32-26-server
drwxr-xr-x 4 root root 1024 2011-01-11 06:44 2.6.32-27-server
drwxr-xr-x 2 root root 1024 2011-02-19 09:05 2.6.32-28-server
```

It seems that my upgrade process is not removing old/unused files?

```
# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-server: Depends: linux-image-2.6.32-28-server but it is not installed
E: Unmet dependencies. Try using -f.
#
# apt-get clean
#
# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
#
# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-27-server linux-headers-2.6.32-24-server linux-headers-2.6.32-24 linux-headers-2.6.32-26
  linux-headers-2.6.32-27 linux-headers-2.6.32-26-server
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.32-30-server linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.32-30-server
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
8 not fully installed or removed.
Need to get 31.5MB of archives.
After this operation, 128MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-server 2.6.32.30.36 [4,508B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-30-server 2.6.32-30.59 [31.5MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-server 2.6.32.30.36 [4,514B]                                 
Fetched 31.5MB in 22s (1,375kB/s)                                                                                                      
(Reading database ... 111028 files and directories currently installed.)
Preparing to replace linux-server 2.6.32.28.32 (using .../linux-server_2.6.32.30.36_amd64.deb) ...
Unpacking replacement linux-server ...
Selecting previously deselected package linux-image-2.6.32-30-server.
Unpacking linux-image-2.6.32-30-server (from .../linux-image-2.6.32-30-server_2.6.32-30.59_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-30-server_2.6.32-30.59_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.32-30-server/kernel/drivers/usb/atm/cxacru.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-server
Found initrd image: /boot/initrd.img-2.6.32-27-server
Found linux image: /boot/vmlinuz-2.6.32-26-server
Found initrd image: /boot/initrd.img-2.6.32-26-server
Found linux image: /boot/vmlinuz-2.6.32-24-server
Found initrd image: /boot/initrd.img-2.6.32-24-server
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
Preparing to replace linux-image-server 2.6.32.28.32 (using .../linux-image-server_2.6.32.30.36_amd64.deb) ...
Unpacking replacement linux-image-server ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-30-server_2.6.32-30.59_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

OK, I ran out of disk space ("no space left on device") and the update failed.

How can I delete or uninstall these old linux images? Especially in the virtual servers, where I can't boot to a live CD?

Thanks for any advice!

---

### Post by andrewthomas on 2011-03-27
As long as 2.6.32-27-server is working good, you should be able to get rid of your other kernels.  

This should free up quite a bit of space.

Also run the```
 apt-get autoremove 
```command

---

### Post by budojeepr on 2011-03-28
> **andrewthomas said:**
> As long as 2.6.32-27-server is working good, you should be able to get rid of your other kernels.

This should free up quite a bit of space.
Strangely enough, I tried it before and it would not let me delete anything (something about an active filesystem). This time it worked.

```
/lib/modules$ ls -l
total 4
drwxr-xr-x 4 root root 1024 2010-09-18 06:49 2.6.32-24-server
drwxr-xr-x 4 root root 1024 2010-11-30 06:27 2.6.32-26-server
drwxr-xr-x 4 root root 1024 2011-01-11 06:44 2.6.32-27-server
drwxr-xr-x 2 root root 1024 2011-02-19 09:05 2.6.32-28-server

sudo rm -rf /lib/modules/2.6.32-24-server
sudo rm -rf /lib/modules/2.6.32-26-server

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             461M  178M  261M  41% /
none                  3.8G  288K  3.8G   1% /dev
none                  3.8G     0  3.8G   0% /dev/shm
none                  3.8G   80K  3.8G   1% /var/run
none                  3.8G     0  3.8G   0% /var/lock
none                  3.8G     0  3.8G   0% /lib/init/rw
```

> Also run the```
 apt-get autoremove 
```command

```
$sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-server: Depends: linux-image-2.6.32-30-server but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-27-server linux-headers-2.6.32-24-server linux-headers-2.6.32-24 linux-headers-2.6.32-26
  linux-headers-2.6.32-27 linux-headers-2.6.32-26-server
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.32-30-server
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.32-30-server
```

S, it worked!

Thanks!

---

### Post by andrewthomas on 2011-03-28
> **budojeepr said:**
> 
```
/lib/modules$ ls -l
total 4
drwxr-xr-x 4 root root 1024 2010-09-18 06:49 2.6.32-24-server
drwxr-xr-x 4 root root 1024 2010-11-30 06:27 2.6.32-26-server
drwxr-xr-x 4 root root 1024 2011-01-11 06:44 2.6.32-27-server
drwxr-xr-x 2 root root 1024 2011-02-19 09:05 2.6.32-28-server

sudo rm -rf /lib/modules/2.6.32-24-server
sudo rm -rf /lib/modules/2.6.32-26-server

```
This is not what you should have done. 
What you needed to do was
```
sudo dpkg -r linux-image-2.6.32-24-server
sudo dpkg -r linux-image-2.6.32-26-server
sudo dpkg -r linux-image-2.6.32-27-server
```

---

