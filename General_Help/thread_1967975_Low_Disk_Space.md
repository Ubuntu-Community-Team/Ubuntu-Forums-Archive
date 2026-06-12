---
title: "Low Disk Space"
date: 2012-04-28
forum: General Help
---

### Post by camikazi2k on 2012-04-28
Getting low desk space message only 7.7mb when people login to the server through thinclients and its kicking them out not allowing them to use any program

sudo fdisk -l

Disk /dev/sda: 146.2 GB, 146163105792 bytes
255 heads, 63 sectors/track, 17769 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000e3d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2               32       17770   142485505    5  Extended

i did sudo apt-get clean and sudo apt-get autoclean

---

### Post by camikazi2k on 2012-04-29
any help

---

### Post by Cheesemill on 2012-04-29
What's the output of:
```
df -h
```

---

### Post by uylug on 2012-04-29
How do you know there are only 7MB free? If the problem is you not having enough space, we can't do anything else but to suggest freeing space.

Post the output of
```
df -h
```

Also, baobab is a nice tool to detect where the space has gone.

```
baobab
```

---

### Post by camikazi2k on 2012-04-29
will do tomorrow when i am in front of it. message keep coming up saying only 7.7mb available

---

### Post by camikazi2k on 2012-04-30
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/oxford--thinserver-root
                      129G   22G  101G  18% /
none                  6.0G  224K  6.0G   1% /dev
none                  6.0G  100K  6.0G   1% /dev/shm
none                  6.0G  356K  6.0G   1% /var/run
none                  6.0G     0  6.0G   0% /var/lock
none                  6.0G     0  6.0G   0% /lib/init/rw
/dev/sda1             228M  208M  7.8M  97% /boot

---

### Post by Cheesemill on 2012-04-30
It's your /boot partition that's nearly full.

If you can try removing any old kernels to free up some space:
[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by camikazi2k on 2012-04-30
ls -lah /boot
total 207M
drwxr-xr-x  4 root root 4.0K 2012-04-23 06:45 .
drwxr-xr-x 22 root root 4.0K 2012-04-23 06:45 ..
-rw-r--r--  1 root root 640K 2010-09-16 14:32 abi-2.6.32-24-generic-pae
-rw-r--r--  1 root root 640K 2011-01-10 20:36 abi-2.6.32-28-generic-pae
-rw-r--r--  1 root root 640K 2011-02-11 15:07 abi-2.6.32-29-generic-pae
-rw-r--r--  1 root root 641K 2011-03-01 21:47 abi-2.6.32-30-generic-pae
-rw-r--r--  1 root root 641K 2011-04-20 19:03 abi-2.6.32-32-generic-pae
-rw-r--r--  1 root root 641K 2011-07-07 23:02 abi-2.6.32-33-generic-pae
-rw-r--r--  1 root root 641K 2011-09-13 21:11 abi-2.6.32-34-generic-pae
-rw-r--r--  1 root root 641K 2011-10-11 16:52 abi-2.6.32-35-generic-pae
-rw-r--r--  1 root root 641K 2011-11-08 20:50 abi-2.6.32-36-generic-pae
-rw-r--r--  1 root root 641K 2011-12-02 21:29 abi-2.6.32-37-generic-pae
-rw-r--r--  1 root root 641K 2012-01-04 09:39 abi-2.6.32-38-generic-pae
-rw-r--r--  1 root root 641K 2012-02-13 21:16 abi-2.6.32-39-generic-pae
-rw-r--r--  1 root root 641K 2012-03-05 19:56 abi-2.6.32-40-generic-pae
-rw-r--r--  1 root root 641K 2012-03-29 13:32 abi-2.6.32-41-generic-pae
-rw-r--r--  1 root root 114K 2010-09-16 14:32 config-2.6.32-24-generic-pae
-rw-r--r--  1 root root 114K 2011-01-10 20:36 config-2.6.32-28-generic-pae
-rw-r--r--  1 root root 114K 2011-02-11 15:07 config-2.6.32-29-generic-pae
-rw-r--r--  1 root root 114K 2011-03-01 21:47 config-2.6.32-30-generic-pae
-rw-r--r--  1 root root 114K 2011-04-20 19:03 config-2.6.32-32-generic-pae
-rw-r--r--  1 root root 114K 2011-07-07 23:02 config-2.6.32-33-generic-pae
-rw-r--r--  1 root root 114K 2011-09-13 21:11 config-2.6.32-34-generic-pae
-rw-r--r--  1 root root 114K 2011-10-11 16:52 config-2.6.32-35-generic-pae
-rw-r--r--  1 root root 114K 2011-11-08 20:50 config-2.6.32-36-generic-pae
-rw-r--r--  1 root root 114K 2011-12-02 21:29 config-2.6.32-37-generic-pae
-rw-r--r--  1 root root 114K 2012-01-04 09:39 config-2.6.32-38-generic-pae
-rw-r--r--  1 root root 114K 2012-02-13 21:16 config-2.6.32-39-generic-pae
-rw-r--r--  1 root root 114K 2012-03-05 19:56 config-2.6.32-40-generic-pae
-rw-r--r--  1 root root 114K 2012-03-29 13:32 config-2.6.32-41-generic-pae
drwxr-xr-x  3 root root 4.0K 2012-04-23 06:45 grub
-rw-r--r--  1 root root 8.3M 2011-02-24 12:03 initrd.img-2.6.32-24-generic-pae
-rw-r--r--  1 root root 8.3M 2011-03-01 06:57 initrd.img-2.6.32-28-generic-pae
-rw-r--r--  1 root root 8.3M 2011-03-02 06:47 initrd.img-2.6.32-29-generic-pae
-rw-r--r--  1 root root 8.3M 2011-03-18 06:52 initrd.img-2.6.32-30-generic-pae
-rw-r--r--  1 root root 8.3M 2011-05-30 06:28 initrd.img-2.6.32-32-generic-pae
-rw-r--r--  1 root root 8.4M 2011-07-15 06:32 initrd.img-2.6.32-33-generic-pae
-rw-r--r--  1 root root 8.4M 2011-09-29 06:49 initrd.img-2.6.32-34-generic-pae
-rw-r--r--  1 root root 8.4M 2011-11-09 06:41 initrd.img-2.6.32-35-generic-pae
-rw-r--r--  1 root root 8.4M 2011-12-02 06:37 initrd.img-2.6.32-36-generic-pae
-rw-r--r--  1 root root 8.4M 2011-12-20 06:39 initrd.img-2.6.32-37-generic-pae
-rw-r--r--  1 root root 8.4M 2012-01-24 06:52 initrd.img-2.6.32-38-generic-pae
-rw-r--r--  1 root root 8.4M 2012-03-06 06:44 initrd.img-2.6.32-39-generic-pae
-rw-r--r--  1 root root 8.4M 2012-03-23 06:39 initrd.img-2.6.32-40-generic-pae
-rw-r--r--  1 root root 8.4M 2012-04-23 06:45 initrd.img-2.6.32-41-generic-pae
drwxr-xr-x  2 root root  12K 2011-02-24 10:03 lost+found
-rw-r--r--  1 root root 157K 2010-03-23 05:37 memtest86+.bin
-rw-r--r--  1 root root 1.7M 2010-09-16 14:32 System.map-2.6.32-24-generic-pae
-rw-r--r--  1 root root 1.7M 2011-01-10 20:36 System.map-2.6.32-28-generic-pae
-rw-r--r--  1 root root 1.7M 2011-02-11 15:07 System.map-2.6.32-29-generic-pae
-rw-r--r--  1 root root 1.7M 2011-03-01 21:47 System.map-2.6.32-30-generic-pae
-rw-r--r--  1 root root 1.7M 2011-04-20 19:03 System.map-2.6.32-32-generic-pae
-rw-r--r--  1 root root 1.7M 2011-07-07 23:02 System.map-2.6.32-33-generic-pae
-rw-r--r--  1 root root 1.7M 2011-09-13 21:11 System.map-2.6.32-34-generic-pae
-rw-r--r--  1 root root 1.7M 2011-10-11 16:52 System.map-2.6.32-35-generic-pae
-rw-r--r--  1 root root 1.7M 2011-11-08 20:50 System.map-2.6.32-36-generic-pae
-rw-r--r--  1 root root 1.7M 2011-12-02 21:29 System.map-2.6.32-37-generic-pae
-rw-r--r--  1 root root 1.7M 2012-01-04 09:39 System.map-2.6.32-38-generic-pae
-rw-r--r--  1 root root 1.7M 2012-02-13 21:16 System.map-2.6.32-39-generic-pae
-rw-r--r--  1 root root 1.7M 2012-03-05 19:56 System.map-2.6.32-40-generic-pae
-rw-r--r--  1 root root 1.7M 2012-03-29 13:32 System.map-2.6.32-41-generic-pae
-rw-r--r--  1 root root 1.2K 2010-09-16 14:34 vmcoreinfo-2.6.32-24-generic-pae
-rw-r--r--  1 root root 1.2K 2011-01-10 20:38 vmcoreinfo-2.6.32-28-generic-pae
-rw-r--r--  1 root root 1.2K 2011-02-11 15:08 vmcoreinfo-2.6.32-29-generic-pae
-rw-r--r--  1 root root 1.2K 2011-03-01 21:49 vmcoreinfo-2.6.32-30-generic-pae
-rw-r--r--  1 root root 1.2K 2011-04-20 19:05 vmcoreinfo-2.6.32-32-generic-pae
-rw-r--r--  1 root root 1.2K 2011-07-07 23:05 vmcoreinfo-2.6.32-33-generic-pae
-rw-r--r--  1 root root 1.2K 2011-09-13 21:14 vmcoreinfo-2.6.32-34-generic-pae
-rw-r--r--  1 root root 1.2K 2011-10-11 16:54 vmcoreinfo-2.6.32-35-generic-pae
-rw-r--r--  1 root root 1.2K 2011-11-08 20:51 vmcoreinfo-2.6.32-36-generic-pae
-rw-r--r--  1 root root 1.2K 2011-12-02 21:31 vmcoreinfo-2.6.32-37-generic-pae
-rw-r--r--  1 root root 1.2K 2012-01-04 09:40 vmcoreinfo-2.6.32-38-generic-pae
-rw-r--r--  1 root root 1.2K 2012-02-13 21:17 vmcoreinfo-2.6.32-39-generic-pae
-rw-r--r--  1 root root 1.2K 2012-03-05 19:57 vmcoreinfo-2.6.32-40-generic-pae
-rw-r--r--  1 root root 1.2K 2012-03-29 13:33 vmcoreinfo-2.6.32-41-generic-pae
-rw-r--r--  1 root root 4.0M 2010-09-16 14:32 vmlinuz-2.6.32-24-generic-pae
-rw-r--r--  1 root root 4.0M 2011-01-10 20:36 vmlinuz-2.6.32-28-generic-pae
-rw-r--r--  1 root root 4.0M 2011-02-11 15:07 vmlinuz-2.6.32-29-generic-pae
-rw-r--r--  1 root root 4.0M 2011-03-01 21:47 vmlinuz-2.6.32-30-generic-pae
-rw-r--r--  1 root root 4.0M 2011-04-20 19:03 vmlinuz-2.6.32-32-generic-pae
-rw-r--r--  1 root root 4.0M 2011-07-07 23:02 vmlinuz-2.6.32-33-generic-pae
-rw-r--r--  1 root root 4.0M 2011-09-13 21:11 vmlinuz-2.6.32-34-generic-pae
-rw-r--r--  1 root root 4.0M 2011-10-11 16:52 vmlinuz-2.6.32-35-generic-pae
-rw-r--r--  1 root root 4.0M 2011-11-08 20:50 vmlinuz-2.6.32-36-generic-pae
-rw-r--r--  1 root root 4.0M 2011-12-02 21:29 vmlinuz-2.6.32-37-generic-pae
-rw-r--r--  1 root root 4.0M 2012-01-04 09:39 vmlinuz-2.6.32-38-generic-pae
-rw-r--r--  1 root root 4.0M 2012-02-13 21:16 vmlinuz-2.6.32-39-generic-pae
-rw-r--r--  1 root root 4.0M 2012-03-05 19:56 vmlinuz-2.6.32-40-generic-pae
-rw-r--r--  1 root root 4.0M 2012-03-29 13:32 vmlinuz-2.6.32-41-generic-pae

---

### Post by camikazi2k on 2012-04-30
uname -r
2.6.32-41-generic-pae

---

### Post by camikazi2k on 2012-04-30
administrator@oxford-thinserver:~$ uname -r
2.6.32-41-generic-pae
administrator@oxford-thinserver:~$ dpkg --list | grep linux-image
ii  linux-image-2.6.32-24-generic-pae    2.6.32-24.43                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-28-generic-pae    2.6.32-28.55                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-29-generic-pae    2.6.32-29.58                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-30-generic-pae    2.6.32-30.59                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-32-generic-pae    2.6.32-32.62                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-33-generic-pae    2.6.32-33.70                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-34-generic-pae    2.6.32-34.77                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-35-generic-pae    2.6.32-35.78                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-36-generic-pae    2.6.32-36.79                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-37-generic-pae    2.6.32-37.81                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-38-generic-pae    2.6.32-38.83                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-39-generic-pae    2.6.32-39.86                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-40-generic-pae    2.6.32-40.87                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-41-generic-pae    2.6.32-41.88                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic-pae              2.6.32.41.48                                    Generic Linux kernel image

---

### Post by Cheesemill on 2012-04-30
I don't know what you're asking?

Just follow the instructions in the link in my previous post.

---

### Post by camikazi2k on 2012-04-30
I can delete all of these below correct

ii  linux-image-2.6.32-24-generic-pae    2.6.32-24.43                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-28-generic-pae    2.6.32-28.55                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-29-generic-pae    2.6.32-29.58                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-30-generic-pae    2.6.32-30.59                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-32-generic-pae    2.6.32-32.62                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-33-generic-pae    2.6.32-33.70                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-34-generic-pae    2.6.32-34.77                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-35-generic-pae    2.6.32-35.78                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-36-generic-pae    2.6.32-36.79                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-37-generic-pae    2.6.32-37.81                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-38-generic-pae    2.6.32-38.83                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-39-generic-pae    2.6.32-39.86                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-40-generic-pae    2.6.32-40.87                                     Linux kernel image for version 2.6.32 on x86

---

### Post by Cheesemill on 2012-04-30
Looks good to me.

If you want to remove all but the newest kernel you can do it with the following command:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs -p sudo apt-get -y purge
```
It will prompt you if you wish to remove the listed kernels, just hit y to continue.

---

### Post by camikazi2k on 2012-04-30
When i do 
sudo apt-get purge linux-image-2.6.32-24-generic-pae 
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.32-24-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 97 not upgraded.
After this operation, 99.3MB disk space will be freed.
Do you want to continue [Y/n]? 


Is that correct command? should i continue

---

### Post by camikazi2k on 2012-04-30
df -hFilesystem            Size  Used Avail Use% Mounted on
/dev/mapper/oxford--thinserver-root
                      129G   21G  102G  17% /
none                  6.0G  232K  6.0G   1% /dev
none                  6.0G  276K  6.0G   1% /dev/shm
none                  6.0G  368K  6.0G   1% /var/run
none                  6.0G     0  6.0G   0% /var/lock
none                  6.0G     0  6.0G   0% /lib/init/rw
/dev/sda1             228M   17M  200M   8% /boot


seems that it did it

thank you

---

### Post by Cheesemill on 2012-04-30
Yes, you need to continue with that and then repeat for all the other kernels you wish to remove.

Alternatively just run the one-line script in my last post to do the same thing.

---

### Post by camikazi2k on 2012-04-30
> **Cheesemill said:**
> Yes, you need to continue with that and then repeat for all the other kernels you wish to remove.

Alternatively just run the one-line script in my last post to do the same thing.

I used the script in your last post. now its pretty much empty

---

### Post by Cheesemill on 2012-04-30
Good, I'm glad we got to the bottom of it :)

Please mark the thread as solved using the 'Thread Tools' button at the top of the page.

---

### Post by WinfriedG on 2012-05-04
deleted and opened as new thread for my problem; sorry

---

