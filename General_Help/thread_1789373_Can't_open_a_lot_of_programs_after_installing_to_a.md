---
title: "Can't open a lot of programs after installing to another partition"
date: 2011-06-23
forum: General Help
---

### Post by Koha23 on 2011-06-23
OK, So I just downloaded Ubuntu to be put on my other partition(I have a C: and a D: drive) So stupid me had a brain fart and ended up not making a new partition and putting Ubuntu on the D: drive which was 3/4 of my total hard drive. So now I have 120 GB for Windows and 350 GB for Ubuntu. So I went to Gparter on Ubuntu and tried to open it and it had an error before it even opened. And when I first went in to Ubuntu it had like 2 things pop up with errors. So I went back to Windows 7 and tried to use the partitioner there and it wouldn't let me expand my C: drive. What am I supposed to do?

---

### Post by LordNeo on 2011-06-23
Boot from a LiveCD, then use GParted to resize the Ubuntu disk, remember to unmount every partition (including swap) from that device before doing anything

---

### Post by Koha23 on 2011-06-23
Well booting from a live CD or Live USB doesn't work for me it comes up with a boot error when I try to run it from the BIOS

---

### Post by LordNeo on 2011-06-23
Boot into the installed and then click the "Test first" button in the first installer window.
If you could reach the installer the first time, there is no reason to not be able to boot live.
Also, you can try GParted disk and several other partition utilities that can boot live

---

### Post by Koha23 on 2011-06-23
Fixed it with this link: [http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/)

---

