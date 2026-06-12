---
title: "How to get Lucid kernel in Karmic"
date: 2009-12-04
forum: General Help
---

### Post by humphreybc on 2009-12-04
Hey I'd like to get the 2.6.32 kernel (released a couple of days ago) in Karmic, to enable 3D on my r600 chipset. I currently have the RC-8 of this kernel - i've been downloading the .debs and installing them from [here.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/")

I want to add the Lucid kernel PPA to my software sources, so that it updates the kernel automatically and plays nicer with stuff like Virtualbox - but the [kernel PPA is empty.]("https://launchpad.net/~kernel-ppa/+archive/ppa")

How do I add the mainline kernel PPA for Lucid Lynx to my Karmic sources, so I get the latest kernels through Update Manager?

Cheers

---

### Post by ENOTTY on 2010-01-10
Hi, if you figured out how to do this, could you post instructions? I'd like to run the .32 kernel to solve some ath9k issues I'm having that even backports don't resolve.

---

### Post by humphreybc on 2010-01-10
Sure, go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Download the headers .deb and the main image .deb that you like and install them :)

---

### Post by darco on 2010-01-10
If you are still seeking an answer, what you can do is change the source.list from any instance of Karmic to Lucid. Reload the repos, then you will be able to d/l the Lucid kernel. After reboot, change the source.list back to the original.



darco

---

### Post by ENOTTY on 2010-01-11
> **humphreybc said:**
> Sure, go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Download the headers .deb and the main image .deb that you like and install them :)

Worked for me. Thanks.

---

### Post by jackdesert on 2010-04-09
> **humphreybc said:**
> Sure, go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Download the headers .deb and the main image .deb that you like and install them :)

Okay, I installed them.. How do I tell Ubuntu to use the new kernel instead of the old one?

-Jack

---

### Post by philinux on 2010-04-09
Did you do a 

```
sudo update-grub
``` ;)

---

### Post by jackdesert on 2010-04-09
> **philinux said:**
> Did you do a 

```
sudo update-grub
``` ;)

It still only lists 2.6.31 kernels in /boot. Am I missing something?

---

### Post by pdoes on 2010-04-17
A little bit more work but you can compile the Lucid kernel and then install the packages.

[http://blog.avirtualhome.com/2010/04/16/compile-and-run-the-ubuntu-lucid-kernel-on-ubuntu-karmic/](http://blog.avirtualhome.com/2010/04/16/compile-and-run-the-ubuntu-lucid-kernel-on-ubuntu-karmic/)

---

