---
title: "Wubi for Linux or: how to install without reboot?"
date: 2009-09-20
forum: General Help
---

### Post by brightbyte on 2009-09-20
It just struck me that having to burn a CD and boot from it in order to run an installer is just silly. But I didn't find a way to simply run the installer program, point it at some free partitions and let it rip - kind of like Wubi does under windows. I mean, ok, i wouldn't be able to repartion, since i have a running OS monted of the disk. But as long as I have some partitions unmounted, or unmountable, why not just let me install to them?

Wubi folks, make a linux edition :) let me apt-get install some-other-version-of-ubuntu! bruning CDs is just so 90s. Thanks :)

update: debootstrap is a good start, but only installs a base system. I want to run the normal installer.

---

### Post by sisco311 on 2009-09-20
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

---

### Post by brightbyte on 2009-09-21
@sisco311: thanks for the links. They both tell me to get around buring a CD, which is nice. But I still don't understand why I would need to reboot at all. Also, but the "FromLinux" approach,I would need at least *two* blank partitions: one to hold the install data and one to install to.

Again: why can I not simply run the installer from my existing linux? Why do I have to boot into a dummy system at all? This seems just silly.

Of course I *can* just burn a CD and boot from it. Nothing keeps me from doing so. I am just trying to understand why it should be necessary, and why nothing nice and simple like Wubi exists for Linux. It just seems ironic.

---

### Post by sisco311 on 2009-09-21
> **brightbyte said:**
> @sisco311: thanks for the links. They both tell me to get around buring a CD, which is nice. But I still don't understand why I would need to reboot at all. Also, but the "FromLinux" approach,I would need at least *two* blank partitions: one to hold the install data and one to install to.


You only need one blank partition, you can use your existing linux partition to store the boot image and the iso.

> **brightbyte said:**
> 
Again: why can I not simply run the installer from my existing linux? 
...
and why nothing nice and simple like Wubi exists for Linux. 


There is [Lubi]("http://lubi.sourceforge.net/lubi.html").

---

