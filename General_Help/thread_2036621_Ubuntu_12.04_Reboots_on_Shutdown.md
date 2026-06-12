---
title: "Ubuntu 12.04 Reboots on Shutdown"
date: 2012-08-02
forum: General Help
---

### Post by neutronforrest on 2012-08-02
Hi Forum,

I am having an issue with a fresh install of Ubuntu 12.04.  I purchased a new intel motherboard

**[FONT=Arial][SIZE=2]Intel BOXDH77KC LGA 1155 Intel H77 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard[/SIZE][/FONT]**

 When I installed Ubuntu everything works great.   However, when I choose shutdown it begins to shutdown.  Then it  pauses..the fans stop..very briefly..and it reboots.  

I think it started doing this when I installed the additional drivers for the graphics driver.  I have tried performing the following.  I go into /etc/default/grub and add acpi=force just after quiet splash.  

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
```I then shutdown the system.  It again reboots but I manually turn off the computer when the purple grub screen comes up.  The system will then shutdown each time after that.  However, after I update and upgrade the system will again just reboot on shutdown.  If I do

```
sudo update-grub
```I then can get the system to shutdown..once I manually shutdown from the purple grub screen.

I hope someone has solved this issue.  Do I just remove the additional driver for the graphics?

Chad

---

