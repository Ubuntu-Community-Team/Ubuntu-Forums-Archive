---
title: "Accidentally deleted the “linux-image-generic”"
date: 2011-05-15
forum: General Help
---

### Post by jsanchezm on 2011-05-15
Hi everyone! Well I tell you that my problem started when upgrading to Ubuntu 11.04. As it happened to me when I updated Ubuntu 10.04 to 10.10, every time I installed something, I got an error when reading "linux-image-generic". That time I solved it by installing a software, called Ubuntu Tweak, with which I deleted all temporary files and old installation packages, and I dont know very well why, it worked and the problem stopped.

This time I tried to do otherwise, and follow the steps that they said in this thread:

[initramfs problem on 11.04 upgrade]("http://askubuntu.com/questions/38083/initramfs-problem-on-11-04-upgrade")

Well, I purged those files and after restarting it tells me:

```
ERROR 15: FILE NOT FOUND
Press any key to continue ...

```

And that gives me to choose between:

```
10.04.1 Ubuntu LTS, Karel-24-generic 06/02/1932

10.04.1 Ubuntu LTS, Karel 06.02.1932-24-generic (Recovered)
```

Any of which leads me back to the Error 15 again.

I started from my old windows partition and using the Ext2fsd to read the linux partition, I could retrieve the file where I had copied the error log that I had when updating, I put it here if it is useful:

```
InstallArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 258222 files and directories currently installed.)
Removing jdownloader ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 1: /etc/default/grub: Permission denied
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.38-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-8-generic; however:
  Package linux-image-2.6.38-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.8.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-2.6.38-8-generic
 linux-image-generic
 linux-generic
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 1: /etc/default/grub: Permission denied
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.38-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-8-generic; however:
  Package linux-image-2.6.38-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.8.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
```

What do I have to do? Is there any way to "put" the files that I deleted back?

---

### Post by Hedgehog1 on 2011-05-15
I might suggest that using the 'windows' side of things you download the ISO for Natty/11.04 and then create a LiveCD or LiveUSB.

With that, you can reload your kernel and anything else that should not have been removed by loading 11.04 again.

When you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE OR ER-INSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

