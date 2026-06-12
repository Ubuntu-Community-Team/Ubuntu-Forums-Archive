---
title: "New Ubuntu User Needs Help (Temperature and Driver Problems)"
date: 2011-08-02
forum: General Help
---

### Post by XxDartagnanxX on 2011-08-02
Hi I'm new to Ubuntu and I need some help with my laptop running at a high temperature,

I checked the CPU usage and it's not high and I cant find any solutions to what I should do. I have a Alienware m11x with Intel i7 processor.

Graphics Card: NVIDIA Geforce Gt 335M
Ram: 4 gigs.
1.20Ghz.

In addition. When i installed my proprietary software under additional drivers (it was the recommended one). My ubuntu will no longer run Unity 3d version. It says my computer can't handle it. 

Please Help with noob computer language. I am in no way advanced.

---

### Post by grahammechanical on 2011-08-02
If you have activated the Nvidia driver then you will be able to use the Unity desktop. When you log in click on your user name and from the menu on the bottom panel select Ubuntu. That is Unity 3D.

Ignore the messages in Additional Drivers that the driver is activated and not in use or that there are no proprietary drivers in use. These messages are inaccurate.

Regards.

---

### Post by pqwoerituytrueiwoq on 2011-08-02
check "hardware drivers" does it say "installed but not active" or something like that
if so you may need to use nomodeset in your kernel's boot line
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```
once that is installed open grub customizer
click the preferences button and at the bottom there is kernel parameters
it will have "quite splash" make it "quite splash nomodeset"
then ok everything
then do this
```
sudo update-grub
sudo reboot
```

---

