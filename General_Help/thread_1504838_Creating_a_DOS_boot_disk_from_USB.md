---
title: "Creating a DOS boot disk from USB"
date: 2010-06-08
forum: General Help
---

### Post by psycho5 on 2010-06-08
Hi

I have a Dell Vostro 1400 with the Nvidia GPU running ubuntu 10.04.

There is a problem with the GPU and dell has recommended that you upgrade your BIOS. I have the executable that can run from either dos or windows. 

The problem is, I can't boot the system long enough before the screen goes blank on me, my option is to boot from a USB disk to a dos command prompt and then execute the update. 

I have the file, I just need instructions on how to create a bootable dos disk using a USB pendrive. 

Where can I get the necessary files to make this happen? All your help is greatly appreciated.


edit : I think I solved the problem on my own

[http://wiki.fdos.org/Installation/BootDiskCreateUSB](http://wiki.fdos.org/Installation/BootDiskCreateUSB)

---

### Post by gmargo on 2010-06-08
I had some problems with that procedure.  I had to add the sectors/head count modification talked about in this script: [http://www.stilen.com/notes/usb_dos_boot.txt](http://www.stilen.com/notes/usb_dos_boot.txt)

---

