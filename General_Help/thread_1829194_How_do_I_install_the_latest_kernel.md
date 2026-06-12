---
title: "How do I install the latest kernel?"
date: 2011-08-20
forum: General Help
---

### Post by linuxuser12345 on 2011-08-20
Hi, I am looking for instructions on how to install the latest 3.0.3 kernel, and I can't seem to find much. I downloaded the necessary files from kernel.org, and they are currently contained in my downloads folder.

How do I install this, now? Is there an easier way, like a PPA option to download and install from?

---

### Post by Duncan Williams on 2011-08-20
It's been deleted from this ppa.
might be to buggy......

[http://www.ubuntuupdates.org/packages/show/360661](http://www.ubuntuupdates.org/packages/show/360661)

---

### Post by Duncan Williams on 2011-08-20
Possible `how to'

[http://www.ramoonus.nl/2011/07/linux-kernel-3-0-0-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/07/linux-kernel-3-0-0-installation-guide-for-ubuntu-linux/)

---

### Post by realzippy on 2011-08-20
for 64bit:

[http://ubuntuforums.org/showpost.php?p=11159514&postcount=38](http://ubuntuforums.org/showpost.php?p=11159514&postcount=38)

for 32 bit you have to replace

amd64
with
i386

---

### Post by linuxuser12345 on 2011-08-20
How do I choose a different kernel at startup?

---

### Post by linuxuser12345 on 2011-08-20
Also, how do I remove the new kernel if I decide I don't like it?

---

### Post by wojox on 2011-08-20
> **linuxuser12345 said:**
> How do I choose a different kernel at startup?
Hold down the left shift key at the grub splash. It should automatically pick it up after you run 

```
sudo update-grub

```
> **linuxuser12345 said:**
> Also, how do I remove the new kernel if I decide I don't like it?

Open synaptic and search for kernel-3.0.

If you installed from a ppa remember to remove it from "Software Update".

---

### Post by realzippy on 2011-08-20
Press "shift" to get to grub when booting,select kernel.
Uninstall it with synaptic or softwarecenter...

---

### Post by linuxuser12345 on 2011-08-20
Thank you! :)

---

