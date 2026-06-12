---
title: "Can't delete my old kernels"
date: 2011-03-08
forum: General Help
---

### Post by C.C.C.P. on 2011-03-08
Hi everyone! 
Since I upgraded from Ubuntu 10.04 to 10.10 I have a couple of old kernels as 2.6.35-22 and 2.6.35-23. So I decided to delete them typed "linux-image" in Synaptic and here's what I got:
> E: linux-image-2.6.35-22-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-23-generic: subprocess installed post-removal script returned error exit status 1I tried to reinstall these two kernels, and again got the same problem. I deleted old kernels from /boot/ and deleted them from /boot/grub/grub.cgf manually. System is working everything is ok, but old kernels still exist in Synaptic, I cant remove them. I think that is the reason why I get "Not all updates can be installed" when I try to update and it forces me to make a partial update. When I open Synaptic I still can see old kernels marked "Mark for Complete Removal". Is there any way to remove them?

---

### Post by Dutch70 on 2011-03-08
Try...

```
sudo apt-get autoremove
```

or installing ubuntu tweak to clean your system.

---

### Post by nomko on 2011-03-08
> **Dutch70 said:**
> Try...
 
```
sudo apt-get autoremove
```
 
or installing ubuntu tweak to clean your system.
 
 
I have very bad experiences with Ubuntu Tweak.
U can remove them by using Synaptic which is way much smarter then using Ubuntu tweak.
 
You know which kernel is in use and you know which has to be removed. Just selected the ones in synaptic who has to be removed. This is the best way to do.

---

### Post by pl@yer on 2011-03-08
See if this will remove them.
```

dpkg --remove --force-remove-reinstreq linux-image-2.6.35-22-generic
dpkg --remove --force-remove-reinstreq linux-image-2.6.35-23-generic

```
or you could manually mess with the post removal scripts and force them to end ok.

---

### Post by philinux on 2011-03-08
There is also this manual method.

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by C.C.C.P. on 2011-03-08
I tried it here is the output it gave me:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libkde3support4 libqt4-qt3support linux-image-2.6.35-22-generic
  linux-image-2.6.35-23-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 283MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 209871 files and directories currently installed.)
Removing linux-image-2.6.35-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 10: irqpoll”: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
/etc/default/grub: 10: irqpoll”: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libkde3support4 ...
Removing libqt4-qt3support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by philinux on 2011-03-08
c.c.c.p,

Post back the results of this.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by celldweller1591 on 2011-03-08
You can try this - Go to Synaptic. In search window write
> header
It will give you currently installed headers. Mark for removal all headers EXCEPT of you current one and last newest header.

---

### Post by C.C.C.P. on 2011-03-08
All ways gave me exactly the same message, solved it by removing old kernels manualy from /var/cache/apt/archives/ and /var/lib/dpkg/info problem is gone everything is ok

---

### Post by domu on 2011-03-09
I have a bash script 'remove-kernel' which I wrote and which I use to list kernels and remove old ones, you can find it under 'My Programs' here: [http://www.timedicer.co.uk/]("http://www.timedicer.co.uk/").

---

### Post by handy on 2011-03-09
I use sudo Worker to delete whatever. Though I use Arch; but what's the difference?

---

