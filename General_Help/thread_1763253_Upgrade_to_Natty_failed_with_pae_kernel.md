---
title: "Upgrade to Natty failed with pae kernel"
date: 2011-05-20
forum: General Help
---

### Post by Paxwax on 2011-05-20
Hi everybody,

I just upgraded Ubuntu from Maverick to Natty. On the GRUB, I now can see there are 2 kernels installed, 2.6.38-8-generic-pae and 2.6.38-8-generic.
The second one works perfectly. But the pae version just shows me the Ubuntu opening screen (with the Ubuntu logo standing over 5 red dots), and then suddenly switches to text mode and displays a prompt. Anybody knows what's the problem?

My computer is a DELL Inspiron 1720. So you don't have to look, inspiron 1720 features Nvidia 8600M GT as graphic chipset, CPU is Intel core 2 duo T7100 @ 1.80GHz, and it has 2Go RAM.

Thanks a lot for your help!

---

### Post by linuxinstalledfromhdd on 2011-05-20
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-2.6.38-8-generic-pae linux-generic-pae linux-headers-generic-pae linux-image-generic-pae linux-headers-2.6.38-8-generic-pae

---

### Post by dargaud on 2011-05-20
I've had lots of problems in the past with PAE kernels interfering with nVidia drivers on Red Hat Enterprise. One solution was to remove the PAE kernels from Grub and /boot. Another (which didn't work at first) is to manually install the nVidia driver.

---

### Post by Paxwax on 2011-05-21
Thanks a lot Linuxinstalledfromhdd, your solution worked perfectly! I guess something didn't work during the first installation, maybe indeed the Nvidia driver, as mentioned by Dargaud.

Anyway, I can now enjoy Natty! :)

---

