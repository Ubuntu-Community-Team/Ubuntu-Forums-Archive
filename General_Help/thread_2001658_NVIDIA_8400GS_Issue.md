---
title: "NVIDIA 8400GS Issue"
date: 2012-06-11
forum: General Help
---

### Post by Johnny420 on 2012-06-11
I have an NVIDIA 8400GS PCIe video card that I would like to use on my Ubuntu 12.04 and am having a hard time getting a driver for it.
 Is this a bug or am I doing it wrong?
Thanks for the help.

---

### Post by deadflowr on 2012-06-11
If your running Ubuntu already, just find the program Additional Drivers, and choose the recommended driver. I run a system with that exact same card and have had no issues, thus far.

---

### Post by Frogs Hair on 2012-06-11
I have the same card in computer I am currently using . Open Additional Drivers and in install the Nvidia current driver.

---

### Post by coffeecat on 2012-06-11
> **Johnny420 said:**
> I have an NVIDIA 8400GS PCIe video card that I would like to use on my Ubuntu 12.04 and am having a hard time getting a driver for it.
 Is this a bug or am I doing it wrong?
Thanks for the help.

I've recently installed 12.04 on two computers each with a nvidia 8400GS card and the Unity 3d desktop works just fine with the default open source nouveau driver. You don't have to install the proprietary driver unless you need better performance for games or suchlike. If you do, as others have said, simply open the additional drivers utility.

---

### Post by oklokl on 2012-06-11
Ubuntu Installation
 Please select F6.

nomodeset

In my case it is used.
my pc 9800 gt
# Ubuntu minimal installation and ...
 Do not install something else

The first is the graphics card.

##  [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

# reboot   (graphics card.  -> Security upgrades at once, Do not install)  If you encounter a bug may cause.
Please reboot after install  ... Security upgrades

---

### Post by coffeecat on 2012-06-11
> **oklokl said:**
> Ubuntu Installation
 Please select F6.

nomodeset

In my case it is used.
my pc 9800 gt

@oklokl, please read my post - the one before yours. I know that nomodeset is needed for some nvidia cards, but it is not for the OP's GeForce 8400GS. The 8400GS "just works" in Ubuntu 12.04. No need for any boot options. No need for the proprietary driver.

---

### Post by deadflowr on 2012-06-11
> **coffeecat said:**
> @oklokl, please read my post - the one before yours. I know that nomodeset is needed for some nvidia cards, but it is not for the OP's GeForce 8400GS. The 8400GS "just works" in Ubuntu 12.04. No need for any boot options. No need for the proprietary driver.

I would agree, it works fine with both open-source and close-source drivers, only bios option I had to change was resetting the graphics card from onboard to pcie, no fiddling with boot options.

---

