---
title: "Karmic boot problems"
date: 2009-12-18
forum: General Help
---

### Post by dasunsrule32 on 2009-12-18
Hello, I really need help, badly. I need my machine up and running. I cannot boot, at all. I am on a dell dimension 9150 with 4gb of ram, nvidia 6800. It has two hard drives, sda and sdb. I am booting from sda, sdb is purely for data storage of my VM's.

I try to boot my machine and it gets just past the white Ubuntu logo and then the screen goes black. I try to boot to recovery mode, it just hangs. I am running kernel: 2.6.31-16-generic from ppa:ubuntu-fastboot, another words, ustart. I can access the file system, so it seems from rescue mode on the alt install cd. Anyone who can help, will be a hero! Thank you in advance.

---

### Post by mikewhatever on 2009-12-18
Do you have other kernels installed, regular, non-ppa ones? If so, does booting any of them work?

---

### Post by dasunsrule32 on 2009-12-22
Some how the Nvidia drivers got corrupted and the xorg.conf was pointing to the nv driver instead of the nvidia driver. I removed all old versions of the nvidia drivers and cleared my apt cache. I then re-downloaded and reinstalled the nvidia-glx-185 package, rebooted and the system was stable again.

I am using the PPA kernels for fastboot and ureadahead, that has not been an issue since I have had the system running, so I am not sure what happened. I looked at my logs and there was an update for the nvidia drivers and the kernel, I installed all at the same time. I should've held the nvidia driver back and then installed it after boot. Anyway, thanks for the reply.:popcorn:

---

