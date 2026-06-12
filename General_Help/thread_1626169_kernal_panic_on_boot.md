---
title: "kernal panic on boot"
date: 2010-11-20
forum: General Help
---

### Post by jfreak_ on 2010-11-20
So I just installed the new linux kernel ( version 26) . On reboot there is a kernel panic with something like not able to mount root fs on 0,0. The older kernel works fine though. And btw while installing the kernel it did complain about not sufficiant space in /boot. I have got this message earlier, so I removed one of the oldest kernels. and i recently there has been package failure during installation of other packages. And one last thing, i noted that during the removal of the older kernel, there were lines in the terminal suggesting that kernel-26 had not been configured properly, so it tried to configure kernel-25 which also apparently failed.

---

### Post by coffee412 on 2010-11-20
> **jfreak_ said:**
> So I just installed the new linux kernel ( version 26) . On reboot there is a kernel panic with something like not able to mount root fs on 0,0. The older kernel works fine though. And btw while installing the kernel it did complain about not sufficiant space in /boot. I have got this message earlier, so I removed one of the oldest kernels. and i recently there has been package failure during installation of other packages. And one last thing, i noted that during the removal of the older kernel, there were lines in the terminal suggesting that kernel-26 had not been configured properly, so it tried to configure kernel-25 which also apparently failed.

Run Fdisk -L and check your partition sizes. Specifically your boot partition. 
If you post the output it will help.

---

### Post by jfreak_ on 2010-11-20
I get this while installing a program. I suspect this is related to the kernel panic.


```

Setting up initramfs-tools (0.98.1ubuntu3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.32-26-generic (2.6.32-26.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-26-generic

gzip: stdout: No space left on device
E: mkinitramfs failure gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.32-26-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-26-generic; however:
  Package linux-image-2.6.32-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up gparted (0.5.1-1ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic

gzip: stdout: No space left on device
E: mkinitramfs failure gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.32-25-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for menu ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-26-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


There is 14.55 mb free of 94 mb size of /boot.

---

### Post by coffee412 on 2010-11-20
> I get this while installing a program. I suspect this is related to the kernel panic.

Open up a term window from the memus (applications/accessories, I believe) and then type in :

fdisk -L > mypartitions.txt 

Then send the created file 'mypartitions.txt' or open it up and copy contents to post. Lets take a quick look at your partitions before anything else.

---

### Post by jfreak_ on 2010-11-20
Apparently fdisk -L is not a command. It gives a suggestion to use
fdisk [options] -l <disk>                            to  list partition table(s)
I tried 
fdisk -l
but this does not give a output.
i have no idea what to put in place of <disk>  . i tried /dev/hda but that is not giving any output, /dev/sda gives a error saying 'unable to open'

---

### Post by jfreak_ on 2010-11-20
Apparently fdisk -L is not a command. It gives a suggestion to use
fdisk [options] -l <disk>                            to  list partition table(s)
I tried 
fdisk -l
but this does not give a output.
i have no idea what to put in place of <disk>  . i tried /dev/hda but that is not giving any output, /dev/sda gives a error saying 'unable to open'

---

### Post by coffee412 on 2010-11-20
> **jfreak_ said:**
> Apparently fdisk -L is not a command. It gives a suggestion to use
fdisk [options] -l <disk>                            to  list partition table(s)
I tried 
fdisk -l
but this does not give a output.
i have no idea what to put in place of <disk>  . i tried /dev/hda but that is not giving any output, /dev/sda gives a error saying 'unable to open'

Should work under all linux systems. 

Here is mine:


> [root@coffee coffee]# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066f96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       30401   243995220   8e  Linux LVM

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e221

Most likely your boot partition is too small. Ive seen this happen before. But interested in seeing some information on your setup before I can really help you. 

If its just not going to boot then boot from the ubuntu cd and choose live version (to run from cd) and then go in and take a look at the partitions like I suggested. 

Gotta know whats going on before we can fix it :p

"That is your misson if you choose to accept it Mr. Phelps":D

---

### Post by jfreak_ on 2010-11-20
well fdisk -l didn't give any results from the live-usb as well. so I have attatched the gparted screenshots.

EDIT:
a sudo was required, so here you are
```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b732b72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19458   156191745    5  Extended
/dev/sda5              13        1472    11717632   83  Linux
/dev/sda6           19333       19458      999424   82  Linux swap / Solaris
/dev/sda7            1472       19332   143466496   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4066 MB, 4066377728 bytes
126 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002912b

```

---

### Post by coffee412 on 2010-11-21
> **jfreak_ said:**
> well fdisk -l didn't give any results from the live-usb as well. so I have attatched the gparted screenshots.

EDIT:
a sudo was required, so here you are
```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b732b72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19458   156191745    5  Extended
/dev/sda5              13        1472    11717632   83  Linux
/dev/sda6           19333       19458      999424   82  Linux swap / Solaris
/dev/sda7            1472       19332   143466496   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4066 MB, 4066377728 bytes
126 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002912b

```

     Device Boot      Start         End      Blocks   Id  System
 /dev/sdb1   *           1       29652   238174208   83  Linux


Your Boot partition looks small. Above is mine. 

Question is - Better to reinstall than start messing with partitions? Well, You can boot from a live cd and change your partitions. But you will have to rerun the grub install. 

I would be tempted to reinstall and just check your partitions before comiting to the install.

:(

---

### Post by jfreak_ on 2010-11-21
Nah no question of re-installing, I have done too much tinkering to be bothered to do it again, and right now it is rock solid (Another reason why I did not go to 10.10). Isn't it easier to just remove the older kernels to free up space? 

And yes /boot is only 100mb.

---

### Post by jfreak_ on 2010-11-21
Removing the older kernels did the trick.
 :-)

---

### Post by coffee412 on 2010-11-21
> **jfreak_ said:**
> Nah no question of re-installing, I have done too much tinkering to be bothered to do it again, and right now it is rock solid (Another reason why I did not go to 10.10). Isn't it easier to just remove the older kernels to free up space? 

And yes /boot is only 100mb.

My boot on Fedora is 121MB. Same difference.

---

### Post by coffee412 on 2010-11-21
> **jfreak_ said:**
> Removing the older kernels did the trick.
 :-)

Great job!

Glad it all worked out for you.

---

### Post by sakura_japan on 2010-11-22
Sorry if i but in, i need some advise regarding that same matter; as i am experiencing the same problem right now. I upgraded from Ubuntu Hardy to 10.10 and ever since i already had this problem in booting. I downloaded an upgrade version of 10.04, and yesterday I bought the physical cd because i thought i can use that to boot into my computer but it was a failure... these are the messages i got:
 
(initramfs) help
 
Built-in commands:
----------------------
 
                         . : [ alias break cd chdir command continue echo eval exec exit
                         export false getopts hash help let local printf pwsd read readonly
                         return set shift source test times trap true type ulimit umask
                         unalias unset wait [  [[  ash awk basename cat chmod chroot chvt
                         clear cmp cp cut deallocvt df du dumpkmap echo egrep env expr
                         false fbset fdflush fgrep find grep gunzip gzip hostname ifconfig
                         ip kill ln loadfont load ls mkdir mkfifo mknod mkswap mktemp
                         more mount mv open vt pidof  printf ps pwd readlink reset rm rmdir
                         sed setkeycodes sh sleep sort stat static-sh stty sync tail tee
                         test touch tr true tty umount uname uniq wc wget yes zcat
 
(initramfs) /init: line 271:  can't open /root/dev/console: no such file
[    44.965051]  Kernel panic - not syncing:  Attempted to kill init!
 
 
can somebody tell me me what command is it after intramfs? Please... have no idea .It's more fun using the computer without getting internally.... yurushiku onegaishimasu:cry:  
 
sakura_japan

---

### Post by coffee412 on 2010-11-22
> **sakura_japan said:**
> Sorry if i but in, i need some advise regarding that same matter; as i am experiencing the same problem right now. I upgraded from Ubuntu Hardy to 10.10 and ever since i already had this problem in booting. I downloaded an upgrade version of 10.04, and yesterday I bought the physical cd because i thought i can use that to boot into my computer but it was a failure... these are the messages i got:
 
(initramfs) help
 
Built-in commands:
----------------------
 
                         . : [ alias break cd chdir command continue echo eval exec exit
                         export false getopts hash help let local printf pwsd read readonly
                         return set shift source test times trap true type ulimit umask
                         unalias unset wait [  [[  ash awk basename cat chmod chroot chvt
                         clear cmp cp cut deallocvt df du dumpkmap echo egrep env expr
                         false fbset fdflush fgrep find grep gunzip gzip hostname ifconfig
                         ip kill ln loadfont load ls mkdir mkfifo mknod mkswap mktemp
                         more mount mv open vt pidof  printf ps pwd readlink reset rm rmdir
                         sed setkeycodes sh sleep sort stat static-sh stty sync tail tee
                         test touch tr true tty umount uname uniq wc wget yes zcat
 
(initramfs) /init: line 271:  can't open /root/dev/console: no such file
[    44.965051]  Kernel panic - not syncing:  Attempted to kill init!
 
 
can somebody tell me me what command is it after intramfs? Please... have no idea .It's more fun using the computer without getting internally.... yurushiku onegaishimasu:cry:  
 
sakura_japan

Can you boot into the live cd and run "sudo fdisk -l" and post it?

You might be in a situation where re-running "grub-install" would work for you. But want to see more about your setup to be sure.

---

