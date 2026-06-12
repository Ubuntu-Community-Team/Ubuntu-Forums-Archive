---
title: "Virtualbox Ubuntu host windows guest usb?"
date: 2011-07-17
forum: General Help
---

### Post by shresthanator on 2011-07-17
Im running windows vista in virtual box on my ubuntu 11.04 machine. I've managed to set up folder sharing between the host and guest but I cannot seem to get the USB working in the windows guest OS. Can someone please help me out?

---

### Post by rickytikki on 2011-07-17
> **shresthanator said:**
> Im running windows vista in virtual box on my ubuntu 11.04 machine. I've managed to set up folder sharing between the host and guest but I cannot seem to get the USB working in the windows guest OS. Can someone please help me out?

have you installed guest additions [http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by shresthanator on 2011-07-17
> **rickytikki said:**
> have you installed guest additions [http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

yes I believe I have, that is how I was able to set up a share folder between my host ubuntu machine and the guest windows. I assumed that you could just plug in a usb device and it would be detected in my guest windows OS....but apparently not.

---

### Post by howefield on 2011-07-17
Try right clicking on the USB activity icon on the bottom right corner of the Virtual Machine window and selecting the appropriate device.

---

### Post by shresthanator on 2011-07-17
> **howefield said:**
> Try right clicking on the USB activity icon on the bottom right corner of the Virtual Machine window and selecting the appropriate device.

Hmm....the usb icon is not there for me....like there is a folder icon and mouse icon and optical driver icon and so on...but there is no usb icon for me to enable/disable....is there something in the settings I have to enable?

---

### Post by howefield on 2011-07-17
I install the .deb package from the VirtualBox site, add myself to the vboxusers group and then install the extension pack.

Then install the VM and guest additions.

If you are using the OSE version of VirtualBox from the repository, it does not support USB. 

It is the extension pack that gives you the closed source code allowing access to USB devices, (amongst some other goodies). I am not sure if adding the extension pack to the OSE version would work.

---

### Post by nothingspecial on 2011-07-17
> **howefield said:**
> install the .deb package from the virtualbox site

+1

---

### Post by shresthanator on 2011-07-17
> **howefield said:**
> I install the .deb package from the VirtualBox site, add myself to the vboxusers group and then install the extension pack.

Then install the VM and guest additions.

If you are using the OSE version of VirtualBox from the repository, it does not support USB. 

It is the extension pack that gives you the closed source code allowing access to USB devices, (amongst some other goodies). I am not sure if adding the extension pack to the OSE version would work.

ok so I've uninstalled Virtual box and I am downloading the deb from the website. How exactly do I install the extension pack?

---

### Post by howefield on 2011-07-17
Download it from the VirtualBox website.

Once you have VirtualBox installed, load up the VirtualBox Manager window and select Preferences from the File Menu, then click on Extensions and then on the top icon to the right of the Extension Packages window, navigate to where you have saved the package and the rest should be self explanatory.

---

### Post by shresthanator on 2011-07-17
> **howefield said:**
> Download it from the VirtualBox website.

Once you have VirtualBox installed, load up the VirtualBox Manager window and select Preferences from the File Menu, then click on Extensions and then on the top icon to the right of the Extension Packages window, navigate to where you have saved the package and the rest should be self explanatory.

thank you, I got it working :)

---

### Post by howefield on 2011-07-17
> **shresthanator said:**
> thank you, I got it working :)

Well done, that's good to know :)

---

