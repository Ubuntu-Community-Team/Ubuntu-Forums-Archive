---
title: "Kernel update problem"
date: 2010-02-06
forum: General Help
---

### Post by The Keeper on 2010-02-06
I have ubuntu box that's running all the time. I noticed that it's boot partition had become full and was unable to install new kernels. I've since removed these kernels by executing
```

sudo apt-get remove --purge 2.6.27-15-* 2.6.27-16-* 2.6.27-17-* 2.6.24-*

```
leaving the only kernel remaining the one the box was running.

However, every time I try to install the latest kernel, this is what happens
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 18.8MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 38038 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-server ...
FATAL: Could not open '/boot/System.map-2.6.24-19-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server
Cannot find /lib/modules/2.6.24-19-server
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And when I try to reinstall the kernel it's complaining about, I get this
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting linux-ubuntu-modules-2.6.24-19-server for regex '2.6.24-19-*'
Reinstallation of linux-ubuntu-modules-2.6.24-19-server is not possible, it cannot be downloaded.
Note, selecting linux-image-2.6.24-19-server for regex '2.6.24-19-*'
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 18.8MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 38038 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-server ...
FATAL: Could not open '/boot/System.map-2.6.24-19-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server
Cannot find /lib/modules/2.6.24-19-server
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What do I need to do to solve this problem?

Thank you in advance. :)

---

### Post by The Keeper on 2010-02-12
Hello? I really could use some help here.

---

### Post by wojox on 2010-02-12
So what does:

```
uname -r
```

say? Did you also run:

```
sudo update-grub
```

---

### Post by The Keeper on 2010-02-12
uname -r: 2.6.27-14-server

I hadn't ran sudo update-grub, but unfortunately it made no difference. :(

---

### Post by The Keeper on 2010-02-12
I searched in google one more time and this time I stumbled upon this topic on this very forum!
[http://ubuntuforums.org/showthread.php?t=831658](http://ubuntuforums.org/showthread.php?t=831658)

And instructions there solved the problem. :)

---

### Post by wojox on 2010-02-12
That's a pretty cool little hack. ;)

---

