---
title: "Updating kernel headers with no internet access"
date: 2011-07-25
forum: General Help
---

### Post by qitch on 2011-07-25
I have ubuntu 10.10 and need to update the kernel headers to get ndiswrapper working,  or so I have been told through searches on getting my problem fixed. I am really not sure how to go about this.

I am trying to get my wna3100 netgear wireless usb to work. After searching for how to do that I think I've got it (ndiswrapper -l shows it), except that when I do "sudo modprobe ndiswrapper" I get "FATAL: Module ndiswrapper not found." Searching showed the solution to be to update the kernel headers and recompile ndiswrapper.

I could easily follow the typical directions, but I only have internet access when in Windows and it isn't really an option to move my computer to the router.

---

### Post by dino99 on 2011-07-25
so use windoz to download what you want, then you can copy/paste or use an usb stick or else to update ubuntu

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

note: you can install one of the latest (3.0.0.7 works fine and the previous too) and you may not need ndiswrapper (maybe)

---

### Post by qitch on 2011-07-25
Thanks. It was more that I wasn't sure what I should download exactly.

---

### Post by dino99 on 2011-07-25
for example:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/)

you have to select either:

 i386, which is 32 bits, but can use >= 4 Gb ram if you install the pae kernel (its my choice for many good reasons), in case your installed system is already a 32 bits

or amd64, which is 64 bits

then you might install:

- linux-headers......all.deb
-linux-headers.......i386.deb  (or amd64.deb)
- linux-image........i386.deb  ("")

and to be sure that the graphic driver will works smoothly, install first "dkms" (sudo apt-get install dkms)

where to download for installing:
- create an empty folder, and put the deb packages there
- goto that folder : cd thisfolder
then:
 sudo dpkg -i *

---

