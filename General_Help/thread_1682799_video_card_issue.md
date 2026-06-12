---
title: "video card issue"
date: 2011-02-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-06
I had a upgraded video card in this machine but i took it out cause of driver issue (gdm crashes on login)
Current integrated card:
```
*-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:feb80000-febfffff ioport:ed98(size=8)
```this is the upgraded card i have
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814139165](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139165) 
since the driver is closed source for that card, there is nothing i can do i assume :mad:
without that upgraded card XP cant have the correct screen resolution
so is there any way to get the drive i915 on to xp so at-lest it will have the proper screen resolution?
once and a while i have to use xp for something and not having the full 1600 900 resolution is a pita
for the record the integrated card works better than the nvida card does with the default drivers on xubuntu 10.04
which is rather depressing if you think about it

---

### Post by dino99 on 2011-02-06
with linux (ubuntu) the kernel directly deal with the needed driver, in your case: xserver-xorg-video-intel.

so if you have a previous xorg.conf using a different driver, you need to:

sudo rm /etc/X11/xorg.conf

---

### Post by pqwoerituytrueiwoq on 2011-02-06
seems either i installed the wrong driver the 1st time or the version changed
i installed nvidia's run file it had some dependence that were not met
```
sudo apt-get install linux-headers-`uname -r` gcc binutils
```also had to blacklist nouveau
```
sudo echo nouveau >> /etc/modprobe.d/blacklist.conf
```then i installed the driver 
make sure gdm is not open (This will close the desktop)
```
sudo service gdm stop
```[Ctrl]+[Alt]+[F1]
```
sudo sh /opt/NVIDIA-Linux-x86-173.14.28-pkg1.run
```then you can reopen gdm 
(if if says nouveau is causing problems reboot to recovery mode and press cancel to get to a tty login)
```
sudo service gdm start
```now if i can find a way to get the tty resolution fixed

you will need to reinstall teh driver after a kernel version update

---

