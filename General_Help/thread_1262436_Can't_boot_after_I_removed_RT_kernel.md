---
title: "Can't boot after I removed RT kernel"
date: 2009-09-09
forum: General Help
---

### Post by Digicraft on 2009-09-09
I dual boot Vista and Ubuntu using EasyBCD and Neogrub. A couple of days ago I installed the RT kernel along with Ubuntu Studio video, audio, graphics, etc. What a major mistake! My system began to freeze regularly, so I decided to get rid of that RT kernel. Using Synaptic while running RT, I (fearfully) removed all files associated with the RT kernel and the new studio packages. I was hoping that my still installed 2.6.28-15-generic kernel would automagically become my boot image. When I subsequently tried to boot up Ubuntu, I got an "unrecognized partition table" error associated with root (hd1,0) where my kernel image lives (or once lived). I followed the advice of someone on the NeoSmart forum and re-configured Neogrub to discover and list my regular 2.6.28-15-generic kernel. But when I selected that kernel for booting, it still failed with the same "unrecognized partition table" error. I fear that I have irreversibly toasted my Ubuntu 9.04 AMD64 installation. Is there some magic I can use to recover? I will be eternally grateful for any help. Thanks.

---

### Post by lidex on 2009-09-10
Try the Super Grub Disk section towards the bottom of this page:
[http://neosmart.net/wiki/display/EBCD/Linux]("http://neosmart.net/wiki/display/EBCD/Linux")

Should probably have a copy of SGD laying around anyway. Download link is on referenced page.

---

### Post by Digicraft on 2009-09-10
I'm in over my head, I think. I'm afraid that SuperGrubDisk Auto will replace my Vista bootloader with GRUB -- don't want that. Do I need to setup GRUB on my Linux partition even though I've been running NeoGrub? I'm a novice when it comes to bootloaders, and I don't want to kill Vista too. My problem is that I don't know what my problem is, only can see symptoms. I have Vista on hd0 and Linux on hd1. I'm going to learn something important here, I just know it.

---

### Post by Digicraft on 2009-09-10
[solved] I removed ".old" extensions on default softlinks to boot image in the root directory. Now my Ubuntu boots as before. Thanks to lidex for pointing me to Super Grub Disk. That helped me boot Linux using the AUTOMAGICAL option. I'm learning!

---

