---
title: "Booting From Separate HD"
date: 2009-12-06
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2009-12-06
I'm currently using Ubuntu 9.04 in VirtaulBox 3.1, but would like to be able to use it without having to run Windows. Problem is, I don't feel comfortable having two different operating systems and different filesystem formats on one hard drive. I was thinking of getting another hard drive exclusively for Ubuntu, what would be better, internal or external?  I'm not sure if I'd be able to choose which HD to boot from if I choose an internal HD.  I thought it might be easier to get an external HD, and just plug it in when I want to use Ubuntu.  I'm pretty sure my PC supports booting from USB, but I'll have to double check.  

** EDIT **  My internal HD connections are SATA, I don't use the older IDE connections.

TIA

---

### Post by oldfred on 2009-12-07
You can do either but it is easier with newer motherboards with SATA drives where you can choose drives in BIOS not reorder drives on the PATA cable or even change jumpers on hard drives.

grub/ubuntu can select drives and boot windows from a second drive without any problem(usually;)). I like installing each operating system to separate drives, so if a drive fails you can switch drives in BIOS and still boot the other operating system. I like making the grub/ubuntu drive first as grub is more flexible at booting other systems, with windows it is difficult to boot anything else without alternate boot loaders or special boot setups. If the windows drive is second in order then grub will not overwrite the windows MBR so you can still boot it.

Also if you can boot from the USB drive you can set up grub on the external to boot it if it is installed or boot windows, or directly boot windows if not plugged in. Check that you can boot the USB. Drive order becomes important, often the external gets promoted to the first drive and that can cause issues but I have seen it done. You just have to keep track of which drive is which as you install and perhaps choose the advanced button near the end of the install to make sure grub is installed to the correct drive. Of course there are instructions on how to fix if not installed correctly, so it is not the end of the world.

---

### Post by decopeland on 2010-01-11
I am running Ubuntu Karmic Koala on internal ssd (32gb) in Asus 900A netbook.  I have installed same on external drive (4gb ssd) in USB enclosure.  I removed the internal drive while installing to external drive.  System will boot from external drive but when I re-install the internal drive it boots from that drive.  BIOS shows the external drive as second boot device behind USB CD-ROM drive.  I want to boot from external drive whenever it is connected and default to internal drive when not connected or have option of selecting boot drive.  Any help?

---

