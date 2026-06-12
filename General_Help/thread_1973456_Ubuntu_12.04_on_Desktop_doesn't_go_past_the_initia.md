---
title: "Ubuntu 12.04 on Desktop doesn't go past the initial screen"
date: 2012-05-04
forum: General Help
---

### Post by thed0ctor on 2012-05-04
Hey guys. I'm trying to install Ubuntu 12.04 LTS onto my desktop computer but it seems like my computer stops recognizing my monitor... 

The initial screen with the keyboard and the guy in the circle shows up for a few seconds, then my monitor cuts off it appears like it's about to reboot but the CD drive sounds as if it's reading things off the disc and the keyboard is still lit so I don't know what's going on... 

I've redownloaded and burned two separate disks and even tried booting from a USB and the same thing happens.

The same disk worked on my laptop just fine.

I built my machine and here are the specifications:

```
Graphics Card: ASUS EAH5830 DIRECTCU/2DIS/1GD5 Radeon HD 5830 1GB

Motherboard: ASUS P6X58D-E Desktop Motherboard

SSD(OS drive): Crucial CTFDDAC128MAG-1G1 128GB 2.5" C300 SATA SSD
HDD: Western Digital Caviar Black WD1002FAEX 1TB (x2)

Processor: Intel i7 950 3.06 GHz

Wireless Card: Rosewill RNX-N300 IEEE 802.11b/g/n Wireless-N 2.0 PCI

DVD Drive: LITE-ON 24X DVD Writer Black SATA Model iHAS424-98
DVD Drive: LG WH10LS30K 10X BLU-RAY BURNER SATA

Card Reader: Koutech IO-RCM621 All-in-one USB 2.0 3.5" USB 2.0

Power Supply: XION Power Real XON-1100P14HE 1100W ATX 12V v2.2 / EPS 12V v2.91 / SSI 2.92 SLI Ready CrossFire Ready

Memory: G.SKILL Ripjaws Series 12GB (3 x 4GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666)

Case: COOLER MASTER HAF X RC-942-KKN1
```

Any suggestions?

Thanks,

Patrick

---

### Post by Rodney9 on 2012-05-04
Burn the discs at the slowest speed you can.

Try a different brand of cd.

Check MD5SUM for your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Try other boot options

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Rodney

---

### Post by thed0ctor on 2012-05-07
Using a different monitor solved the problem and then I had several graphical issues that were remedied by installing the proprietary drivers.

---

