---
title: "Boot Partition is Full"
date: 2010-02-08
forum: General Help
---

### Post by 1awesomeguy on 2010-02-08
I have a total of four partitions on my Ubuntu 9.10 (Karmic) system:

sda1 = /boot
sda2 = /
sda3 = swap
sda4 = /home

My boot partition is 94 MiB which I was recommended would be more than enough space. Turns out my /boot partition is full and I now get a message every time I log into Ubuntu saying, 'The volume "boot" has only 0 bytes disk space remaining.' Also after installing GParted to check up on my partitions I got the following error in apt-get:

```
Setting up gparted (0.4.5-2ubuntu1) ...

Setting up kpartx (0.4.8-14ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.31-19-generic
dpkg: subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I have no experience messing around in my /boot partition besides modifying GRUB. I think most likely I just have too many kernel versions installed in the /boot partition? Can anyone advise me on what to do here?

Thanks!

---

### Post by drs305 on 2010-02-08
> **1awesomeguy said:**
> 
I have no experience messing around in my /boot partition besides modifying GRUB. I think most likely I just have too many kernel versions installed in the /boot partition? Can anyone advise me on what to do here?

Thanks!

If you give us the contents of your boot folder we can tell you what you can remove to free up some space. The second command will tell us which kernel you are currently using:
```

ls -lah /boot
uname -r

```

---

### Post by darolu on 2010-02-08
Try removing kernel images that you no longer use. Open Synaptic and search for linux-image-2, the ones with the box checked are the installed ones, remove all of them but the one you are using (uname -r) and the previous one (just in case). I have 1 kernel only and my /boot is around 14MB, so doing this may solve your problem.

---

### Post by 1awesomeguy on 2010-02-08
Thanks for the help so far, guys!

> **drs305 said:**
> If you give us the contents of your boot folder we can tell you what you can remove to free up some space. The second command will tell us which kernel you are currently using:
```

ls -lah /boot
uname -r

```

```
chris@jessica:~$ ls -lah /boot
total 82M
drwxr-xr-x  4 root root 3.0K 2010-02-08 16:50 .
drwxr-xr-x 21 root root 4.0K 2010-02-08 16:43 ..
-rw-r--r--  1 root root 615K 2009-10-16 14:03 abi-2.6.31-14-generic
-rw-r--r--  1 root root 615K 2009-11-10 13:52 abi-2.6.31-15-generic
-rw-r--r--  1 root root 615K 2009-12-08 03:03 abi-2.6.31-16-generic
-rw-r--r--  1 root root 615K 2009-12-10 14:33 abi-2.6.31-17-generic
-rw-r--r--  1 root root 615K 2010-01-08 13:54 abi-2.6.31-18-generic
-rw-r--r--  1 root root 615K 2010-01-27 23:39 abi-2.6.31-19-generic
-rw-r--r--  1 root root 109K 2009-10-16 14:03 config-2.6.31-14-generic
-rw-r--r--  1 root root 109K 2009-11-10 13:52 config-2.6.31-15-generic
-rw-r--r--  1 root root 109K 2009-12-08 03:03 config-2.6.31-16-generic
-rw-r--r--  1 root root 109K 2009-12-10 14:33 config-2.6.31-17-generic
-rw-r--r--  1 root root 109K 2010-01-08 13:54 config-2.6.31-18-generic
-rw-r--r--  1 root root 109K 2010-01-27 23:39 config-2.6.31-19-generic
drwxr-xr-x  2 root root 5.0K 2010-02-06 12:04 grub
-rw-r--r--  1 root root 7.7M 2009-11-16 23:13 initrd.img-2.6.31-14-generic
-rw-r--r--  1 root root 7.7M 2009-11-17 00:16 initrd.img-2.6.31-15-generic
-rw-r--r--  1 root root 7.7M 2009-12-18 00:30 initrd.img-2.6.31-16-generic
-rw-r--r--  1 root root 7.7M 2010-01-08 21:53 initrd.img-2.6.31-17-generic
-rw-r--r--  1 root root 7.7M 2010-01-29 00:01 initrd.img-2.6.31-18-generic
-rw-r--r--  1 root root 7.7M 2010-02-06 12:03 initrd.img-2.6.31-19-generic
drwx------  2 root root  12K 2009-11-16 23:04 lost+found
-rw-r--r--  1 root root 126K 2009-10-23 12:11 memtest86+.bin
-rw-r--r--  1 root root 1.6M 2009-10-16 14:03 System.map-2.6.31-14-generic
-rw-r--r--  1 root root 1.6M 2009-11-10 13:52 System.map-2.6.31-15-generic
-rw-r--r--  1 root root 1.6M 2009-12-08 03:03 System.map-2.6.31-16-generic
-rw-r--r--  1 root root 1.6M 2009-12-10 14:33 System.map-2.6.31-17-generic
-rw-r--r--  1 root root 1.6M 2010-01-08 13:54 System.map-2.6.31-18-generic
-rw-r--r--  1 root root 1.6M 2010-01-27 23:39 System.map-2.6.31-19-generic
-rw-r--r--  1 root root 1.2K 2009-10-16 14:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r--  1 root root 1.2K 2009-11-10 13:55 vmcoreinfo-2.6.31-15-generic
-rw-r--r--  1 root root 1.2K 2009-12-08 03:05 vmcoreinfo-2.6.31-16-generic
-rw-r--r--  1 root root 1.2K 2009-12-10 14:35 vmcoreinfo-2.6.31-17-generic
-rw-r--r--  1 root root 1.2K 2010-01-08 13:56 vmcoreinfo-2.6.31-18-generic
-rw-r--r--  1 root root 1.2K 2010-01-27 23:41 vmcoreinfo-2.6.31-19-generic
-rw-r--r--  1 root root 3.8M 2009-11-17 02:58 vmlinuz-2.6.31-14-generic
-rw-r--r--  1 root root 3.8M 2009-11-10 13:52 vmlinuz-2.6.31-15-generic
-rw-r--r--  1 root root 3.8M 2009-12-08 03:03 vmlinuz-2.6.31-16-generic
-rw-r--r--  1 root root 3.8M 2009-12-10 14:33 vmlinuz-2.6.31-17-generic
-rw-r--r--  1 root root 3.8M 2010-01-08 13:54 vmlinuz-2.6.31-18-generic
-rw-r--r--  1 root root 3.8M 2010-01-27 23:39 vmlinuz-2.6.31-19-generic
```

```
chris@jessica:~$ uname -r
2.6.31-19-generic
```

> **darolu said:**
> Try removing kernel images that you no longer use. Open Synaptic and search for linux-image-2, the ones with the box checked are the installed ones, remove all of them but the one you are using (uname -r) and the previous one (just in case). I have 1 kernel only and my /boot is around 14MB, so doing this may solve your problem.

When I try to open Synaptic, I get an error:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When trying to run the command:

```
chris@jessica:~$ sudo dpkg --configure -a
[sudo] password for chris:
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.31-19-generic
dpkg: subprocess installed post-installation script returned error exit status 1

```


Should I gksu nautilus into my /boot folder and delete the kernel-looking files minus the last two? Is there any way to have the computer automatically delete old kernels without me needing to do this every so often?

---

### Post by darolu on 2010-02-09
It may be risky but you have no choice but to delete some kernel files manually from your /boot, delete 14 to 17 series, that should give you enough room for dpkg to work; after you deleted the files try the "sudo dpkg --configure -a" command so you can finally uninstall unnecesary kernels.

I don't know of an automatic way to delete kernels.

---

### Post by rnerwein on 2010-02-09
hi
before i'll remove the unused kernel i will try to move them to your /home and then if you got enough space on /boot move one back to /boot  and them remove them via. 
apt-get remove or dpkg.
step by step
ciao

---

### Post by drs305 on 2010-02-09
1awesomeguy,

Do this to get get some space in /boot. The command will move the -14 files in /boot to your Desktop. That should give you enough room for APT to work.  If you need more room, change 14 to 15 and run the command again:
```
sudo mv /boot/*2.6.31-14* ~/$HOME/Desktop 
```

Once you get APT (Synaptic/dkpg/etc) working again, you can safely remove the 15, 16 & 17 kernels. In Synaptic, do a search for "2.6.31-" and remove the associated the *linux-image and linux-headers* packages.

Next, move the -14 files back into /boot and again remove them via Synaptic. This will cleanly remove them and remove root files from remaining on your Desktop or in the trash bin:
```
sudo mv ~/Desktop/*2.6.31-14* /boot
```

---

### Post by 1awesomeguy on 2010-02-10
drs305's solution seems to have solved my problems. Is there any way to get the system to automatically uninstall unused kernels?


Here is how I solved the problem for anyone else having the same issue:

**In Terminal:**
```
sudo mv /boot/*2.6.31-14* ~/Desktop
sudo dpkg --configure -a
```

Output:
```
chris@jessica:~$ sudo mv /boot/*2.6.31-14* ~/Desktop
chris@jessica:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
```

**In Synaptic:**
Complete Removal of the following packages:
linux-image-2.6.31-15-generic
linux-image-2.6.31-16-generic
linux-image-2.6.31-17-generic
linux-headers-2.6.31-15
linux-headers-2.6.31-16
linux-headers-2.6.31-17
linux-headers-2.6.31-15-generic
linux-headers-2.6.31-16-generic
linux-headers-2.6.31-17-generic

**In Terminal:**
```
sudo mv ~/Desktop/*2.6.31-14* /boot
```

**In Synaptic:**
Complete Removal of the following package:
linux-image-2.6.31-14-generic

**Result:**
/boot partition with 55.56 MiB free space

---

### Post by drs305 on 2010-02-10
> **1awesomeguy said:**
> drs305's solution seems to have solved my problems. Is there any way to get the system to automatically uninstall unused kernels?

There is no automatic way to remove them via an app. You could write a script that could do it.

There are various ways to "hide" the extra kernels - StartUp-Manager for Grub legacy and editing the /etc/grub.d/10_linux script in Grub 2. These would probably not be good options for you since you would probably want to know how many kernels you have accumulating in your /boot folder.

As far as removing kernels in the future, I recommend Ubuntu Tweak. It's an app that can make several useful changes to Ubuntu settings via a GUI interface. One of the tweaks is removing extra kernels. It is painless and won't show the kernel in use, so it is pretty safe to use.

You may also consider moving /boot back into your normal installation. Unless you have a specific reason to have a separate /boot folder it isn't really necessary for most users. Moving it back into your / folder will eliminate the need to remove older kernels as frequently.

Another option would be to expand your /boot partition from the LiveCD using Gparted. 

Or just keep a closer eye on your /boot folder. As you found you can accumulate 4-6 kernels before running out of room. Since you only need to keep a couple, you have a bit of a buffer now that you are aware of your disk space situation.

---

### Post by sprosty on 2012-02-24
If you just delete files from your boot directory you will be leaving other related files in /lib and possibly other directories as well. 

Each upgrade seems to amount to 99-125MB so these can add up quickly. 

The best method I've found so far to clean up your boot partition as well as removing previous installed kernels is discussed on [this ubuntuformums post]("http://ubuntuforums.org/showpost.php?p=11509012&postcount=2") - and that post refers [here]("http://www.upubuntu.com/2011/11/how-to-remove-unused-old-kernels-on.html"). 

I've used a modified version of the instructions (shown below) successfully on my own servers. 

[LIST=1]
[*]```
uname -r
```
[*]```
dpkg --list | grep linux-image
```
[/LIST]

I then pick the oldest linux-image name from the dpkg output (e.g. linux-image-2.6.32-27-generic-pae) and then run: 

```
sudo aptitude purge linux-image-2.6.32-27-generic-pae
```

That's it. 

Messing with boot partitions and kernels makes me nervous, so I'd rather be conservative. I personally like this approach better as I'm only removing one kernel at a time. Also if you watch aptitude it runs "/usr/sbin/update-grub" for me so I do not run the "sudo update-grub2" as recommend in the link above. 

fyi man update-grub2: 

> update-grub2 is a stub for running update-grub which itself is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to
       generate a grub2 config file.

---

### Post by MichaelGld on 2012-03-06
> **drs305 said:**
> There is no automatic way to remove them via an app. You could write a script that could do it.

There are various ways to "hide" the extra kernels - StartUp-Manager for Grub legacy and editing the /etc/grub.d/10_linux script in Grub 2. These would probably not be good options for you since you would probably want to know how many kernels you have accumulating in your /boot folder.

As far as removing kernels in the future, I recommend Ubuntu Tweak. It's an app that can make several useful changes to Ubuntu settings via a GUI interface. One of the tweaks is removing extra kernels. It is painless and won't show the kernel in use, so it is pretty safe to use.

You may also consider moving /boot back into your normal installation. Unless you have a specific reason to have a separate /boot folder it isn't really necessary for most users. Moving it back into your / folder will eliminate the need to remove older kernels as frequently.

Another option would be to expand your /boot partition from the LiveCD using Gparted. 

Or just keep a closer eye on your /boot folder. As you found you can accumulate 4-6 kernels before running out of room. Since you only need to keep a couple, you have a bit of a buffer now that you are aware of your disk space situation.
I have made a mess of my GRUB menu. It lists a bunch of kernels, some of which may not exist. What's weird too is that Ubuntu Tweak shows under Clean Kernels *no kernels* - it's completely empty. However when I select Clean Config and scroll down, I can see a few kernels listed there. Any ideas?

---

### Post by drs305 on 2012-03-07
> **MichaelGld said:**
> I have made a mess of my GRUB menu. It lists a bunch of kernels, some of which may not exist. What's weird too is that Ubuntu Tweak shows under Clean Kernels *no kernels* - it's completely empty. However when I select Clean Config and scroll down, I can see a few kernels listed there. Any ideas?

I can think of a couple of things to check. If Ubuntu Tweak doesn't show any kernels, it probably isn't finding any kernels but the one it use (which it won't list). 

Do you have several installations of Ubuntu on your computer? It's possible Grub is finding kernels from another partition. It is also possible it is 'mining' the entries from old Grub menus that are still on your system. When Grub probes for other OS's, it can lift entries from other Grub menus as well as add kernels it finds on other partitions.

One thing you can check is where these kernels are listed in the grub menu (/boot/grub/grub.cfg). That file is broken down into sections - 10_linux is your current OS, while the 30_os-prober searches other partitions. Finding which section the extraneous entries are in can help pinpoint the partition to investigate further.

---

