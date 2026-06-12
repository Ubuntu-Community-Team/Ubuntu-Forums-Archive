---
title: "NVIDIA Optimus and VM Ubuntu?"
date: 2010-11-21
forum: General Help
---

### Post by kubkub on 2010-11-21
Hello,

I'm going to purchase a new laptop soon. The one I have decided to get has NVIDIA Optimus, I've searched around and found that it can have problems when booting into Ubuntu... Has anyone had problems with using virtual machines? I am wondering if it works fine if I use Ubuntu 10.04 with VM Player? If anyone has tried please give feedback. :)


Thanks.

---

### Post by WienerWuerstel on 2010-11-21
Nvidia doesn't support Optimus on Linux. So if you like Linux and want to use it on a Laptop you should get one with an AMD or Intel Graphics Chip.

---

### Post by kubkub on 2010-11-21
WienerWuerstel, did you actually test it yourself?

I know there is no support for Optimus. But, as far as I understood Optimus allows the switching of discrete and integrated graphics, you actually have a NVIDIA and an Intel and you can switch to use either. Optimus doesn't support XP or Vista or Linux in the aspect of being able to go through both. So with that into perspective, has anyone ran Ubuntu in a **virtual machine** on Windows 7 successfully?


[http://www.anandtech.com/show/2934/nvidia-optimus-truly-seamless-switchable-graphics-and-asus-ul50vf/11](http://www.anandtech.com/show/2934/nvidia-optimus-truly-seamless-switchable-graphics-and-asus-ul50vf/11)

Here it is said to run, but that's by hard booting.

---

### Post by WienerWuerstel on 2010-11-21
I didn't say that it doesn't work at all. I am just saying that if you run Linux on an Optimus Laptop you can only use the Intel Graphics Chip and the Nvidia Graphics Chip will only eat Battery Life away and you can't turn it off. It will be probably be the same with Virtualbox/Vmware. So yes, it would work (kinda) but it would not make much Sense because of the Reasons i stated above. But that is just my Opinion.

---

### Post by kubkub on 2010-11-21
I run Ubuntu in a virtual box for a reason, mainly since I'm not willing to make a full switch from Windows. I'm not concerned about battery life, I'm practically always plugged in. Considering its inside Windows I multitask accordingly with VM, and as I know, the user can choose which card to run for each program in the system. I'm not looking for an opinion, where you think that it "kinda" works. I want facts on how it responds. Specifically if there are any notable conflicts with using VM, I need a properly working OS to do Linux assignments and testing. For anyone that has actual experience with running Ubuntu via virtual machine with Optimus, shed some light please.

---

### Post by strikeoncmputrz on 2010-11-22
KubKub, I have been running Ubuntu both in a Virtualbox VM and natively on a partition on my Alienware M11x which has optimus. Ubuntu runs fine in both. There are some big caveats however. In the VM you cannot enable composting since Virtualbox doesn't support 2d acceleration for linux yet.  Natively, ubuntu can only run graphics through the integrated CPU. The Nvidia card stays on but will not actually do anything for you.

---

