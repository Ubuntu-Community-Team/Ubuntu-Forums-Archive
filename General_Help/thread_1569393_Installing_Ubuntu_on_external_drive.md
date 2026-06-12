---
title: "Installing Ubuntu on external drive"
date: 2010-09-06
forum: General Help
---

### Post by bootneck02 on 2010-09-06
:pI am  thinking of installing Ubuntu 64 Bit on an external drive my system is as follows:-
PC: home build Case:Antec 300
PSU: Cooler Master Real Power M700TFT
Screen: ASUS VH226 21.7
Mother Board;Asus P5Q Deluxe
CPU: Intel Core 2 Quad Q8200 2.33GHz 1333FSB (Retail 775)
RAM:    GeIL Black Dragon 8GB (4x2GB) DDR2 PC2-8500C5 1066MHz Dual Channel Kit  
O S:Microsoft 7 Ultimate 64 bit
Speakers: Sony SRSD211.CEK 2.1 35W  
Sound Card: Auzen X-Meridian (Dam good it is to worth every penny)
Video Card: Saphire HD4870 Toxic 1GB  
Hard Discs:   SAMSUNG HD154UI  (1500.30 GB)

I am quite happy with Windows 7 and briefly have dabbled with Ubuntu 32 bit dual boot some time ago running XP Pro, but would want to eventually once I had got used to using Ubuntu change over to it as my OS as I am fed up filling up Microsoft coffers.
So my questions are:
1)Can I put Ubuntu on a external drive rather dual boot on the C drive.
2)Are drivers available for all my hardware, printer and web cam.
3)What are the security risks with Ubuntu as far as Viruses, spyware etc.
4)Will the PC recognise there are two OS when the external drive is connected via USB prior to booting up.
If you could reply in simple terms as I have knowledge of softeware writing and just a simpleton as far as software is concerned. ):P

---

### Post by 67GTA on 2010-09-06
You can run the live CD to see if everything is compatible. You can check for sound, do a printer test, etc. Most drivers are already on the CD if they are available. It is not like Windows where you have to chase down drivers after install. There are certainly cross platform viruses/malware, but because of the way Linux security is set up, you shouldn't have to worry. Just be sure to stick to software from trusted repositories. The Linux kernel has a firewall built in with sane defaults. Ubuntu uses the grub bootloader. You can choose the advanced or manual install and choose where to put the OS (external drive), as well as the bootloader. This will let you keep your internal drive as is, and only see the Ubuntu grub bootloader when you boot from the external drive. The manual install requires that you have a little knowledge of hard dive partitions.

---

### Post by oldfred on 2010-09-06
Just realize the external will not be quite as fast since it is external.

You also need to make sure you install grub to the external using the advanced button during the install:

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

