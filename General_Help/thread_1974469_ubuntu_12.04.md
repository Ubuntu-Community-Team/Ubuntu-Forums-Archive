---
title: "ubuntu 12.04"
date: 2012-05-06
forum: General Help
---

### Post by malpas on 2012-05-06
hi i am using ubuntu 12.04 and running windows 7 through vitual box but when i try to upgrade the standard vga driver that 7 installs with the current nvidia drivers for my geforce 260 graphics card the driver install checks for compatabilty and says unable to find the hardware ie the graphics card, but I had no problem installing the nvidia drivers in Ubuntu):P

---

### Post by Cheesemill on 2012-05-06
This is because virtual machines cannot see the actual graphics you have in your computer. Instead they see a virtual graphics card that is presented to them by VirtualBox.

To install the drivers for this virtual graphics card you need to install the VirtualBox guest additions in your WIndows VM, to do this just go to Device > Install Guest Additions while your VM is running.

---

### Post by malpas on 2012-05-07
Many thanks for the quick reply,?being a newbie to ubuntu do you mean install guest additons whilst the os is running in VB or after i have installed VB program.

---

### Post by Cheesemill on 2012-05-07
Install them in your running Windows 7 guest.

[http://www.howtogeek.com/howto/2845/install-guest-additions-to-windows-and-linux-vms-in-virtualbox/](http://www.howtogeek.com/howto/2845/install-guest-additions-to-windows-and-linux-vms-in-virtualbox/)
[http://www.youtube.com/watch?v=vi53zKcvgXU&noredirect=1](http://www.youtube.com/watch?v=vi53zKcvgXU&noredirect=1)

---

