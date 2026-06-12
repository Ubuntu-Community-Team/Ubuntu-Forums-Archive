---
title: "kernel update error"
date: 2010-06-03
forum: General Help
---

### Post by jdunn on 2010-06-03
This morning, Update manager downloaded and attempted to install linux kernel image and header files but failed with some sort of error.  I'm trying to locate the error log for synaptic package manager.  Anyway I rebooted and everything seems to work okay.  Did anyone else have this problem?  This is from the history:


```
Commit Log for Thu Jun  3 05:45:42 2010


Upgraded the following packages:
linux-headers-2.6.32-22 (2.6.32-22.33) to 2.6.32-22.35
linux-headers-2.6.32-22-generic (2.6.32-22.33) to 2.6.32-22.35
linux-image-2.6.32-22-generic (2.6.32-22.33) to 2.6.32-22.35
linux-libc-dev (2.6.32-22.33) to 2.6.32-22.35
```

---

### Post by Soul-Sing on 2010-06-03
i had several server errors, and had troubles installing the updates. (very slow updates)

---

### Post by wojox on 2010-06-03
> **leoquant said:**
> (very slow updates)

Good to know, I thought it was just me that was happening to.

---

### Post by RambJoe on 2010-06-03
These kernel files are old, 2.6.34 is out, anyone know why the update manager is trying to install them?

---

### Post by jdunn on 2010-06-03
where is the log file?

---

### Post by cbrunhaver on 2010-06-03
I had the same issue (error 127) when trying to install this kernel from the update manager.  Still, thing seem to be working fine.

What log file would you need (a dpkg log or something)?
\

---

### Post by jdunn on 2010-06-04
> **cbrunhaver said:**
> I had the same issue (error 127) when trying to install this kernel from the update manager.  Still, thing seem to be working fine.

What log file would you need (a dpkg log or something)?
\

That's exactly the error I got yesterday.  Today, the same thing.  This morning I got an update notice from package manager for a linux kernel update.  I got an error on installation.  This time, I copied the details:

```
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic

Setting up linux-libc-dev (2.6.32-22.36) ...
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-22.33 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash&#8221;: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
```

I rebooted and everything seems to work fine, except I had to fill out a crash report.  There was a timeout error when reporting the bug on the web.  My top panel is now screwed up but, I don't see how that can be related.

---

### Post by cbrunhaver on 2010-06-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/589163](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/589163)

---

### Post by jdunn on 2010-06-05
still having problems.  I installed the openal1 package, which updated the kernel.  Again, I got the error exit status 127

---

### Post by XSAlliN on 2010-06-05
> **RambJoe said:**
> These kernel files are old, 2.6.34 is out, anyone know why the update manager is trying to install them?

Not old, yet .34 is newer but won't be added to Lucid any time soon. Lucid is based on .32 so they'll decide what en when.  You might see.37 available and by that time Lucid still on .33 or maybe .34

> still having problems. I installed the openal1 package, which updated the kernel. Again, I got the error exit status 127

Chose a different download Server.

---

### Post by nss0000 on 2010-06-05
> **jdunn said:**
> still having problems.  I installed the openal1 package, which updated the kernel.  Again, I got the error exit status 127

Various Ubuntu updates are trashing anything they touch. My 8.04.1 got hosed and 10.04 breaks something new every time. 

Currently ... Ubuntu is toxic.

---

### Post by jdunn on 2010-06-08
Same message after today's update.

```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for python-support ...
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-22.33 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.32-22-generic

```

---

