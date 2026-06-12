---
title: "Big Doubt"
date: 2012-06-12
forum: General Help
---

### Post by sohail webconnect on 2012-06-12
How do i disable only GRUB boot-loader updates?? I wanna disable it cause I have dual-booted UBUNTU 10.04.4(64 bit) with windows 7(32 bit) on my PC to set up the android development environment and i have heard that if the boot loader is updated then the windows entry in the boot-loader is lost and the we have to install windows completely from scratch in a separate partition to get the windows boot loader and access the previous installation!!

How to download Nvidia graphics card driver for Ubuntu??

Any good guides on terminal commands(I'm familiar with windows cmd)??

When i try to get administrator rights in the terminal using su command and enter the correct password i get authentication failed error

---

### Post by wilee-nilee on 2012-06-12
> **sohail webconnect said:**
> How do i disable only GRUB boot-loader updates?? I wanna disable it cause I have dual-booted UBUNTU 10.04.4(64 bit) with windows 7(32 bit) on my PC to set up the android development environment and i have heard that if the boot loader is updated then the windows entry in the boot-loader is lost and the we have to install windows completely from scratch in a separate partition to get the windows boot loader and access the previous installation!!

How to download Nvidia graphics card driver for Ubuntu??

Any good guides on terminal commands(I'm familiar with windows cmd)??

When i try to get administrator rights in the terminal using su command and enter the correct password i get authentication failed error

The only time a grub update would be held back is in a wubi install, is that what you have.

I believe that this is not a problem any more.

As far as having to reinstall windows to get it back in case grub was put in the mbr that is plain hogwash.

Nvidia commands.

```
sudo apt-get install nvidia-current
```
 ```
sudo apt-get install --reinstall nvidia-current 
```

Use sudo not su

---

