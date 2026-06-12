---
title: "Problems finding the USB devices in Virtual box"
date: 2011-04-10
forum: General Help
---

### Post by Sea Otter on 2011-04-10
I have installed the Virtual box as recommended direct from the Oracle website, also downloaded the extension pack. The filter installed in VBox as Ubuntu (the host) found all connected devices. Yet when starting the guest OS in my case Win XP Pro. (the XP is installed and works excellent with all programs I have installed on that OS. It is just a problem for the virtual XP to find any USB device. Anyone having a solution on this?

I have done the step by step checking according to the manual from Oracle about Virtual box with the extension kit installed. It seems to be a standing problem with all emulators, more or less. Anyway, I need urgent help on this. Thank for all inputs in advance.

Chris

---

### Post by matty abbo on 2011-04-10
are you sure the settings in the virtual program allows the guest OS to use USB devices?

---

### Post by Sea Otter on 2011-04-10
> **matty abbo said:**
> are you sure the settings in the virtual program allows the guest OS to use USB devices?

Yes, because when you set up USB in the Virtual machine settings, you have to add a "filter". That filter is just to say that the host machine has found this device and now I am adding this to the Virtual Machine i.e. the guest and in my case Win XP Pro. Check this link to Oracle [http://www.virtualbox.org/manual/ch03.html#settings-usb](http://www.virtualbox.org/manual/ch03.html#settings-usb)  

There is also this one [http://www.virtualbox.org/manual/ch03.html#settings-usb](http://www.virtualbox.org/manual/ch03.html#settings-usb) 

After reading those (if you have time and interest) and youu find out something I have not understood, please help me.

Chris

---

### Post by matty abbo on 2011-04-10
mhmm, i am not really sure but just wondering if checking for updates and applying them would work, but if not then i am stumped, sorry

---

### Post by GridLynx on 2011-04-21
Hey there Otter

I seem to be having the same problem as you. Only my USB devices show as " Unavailable" in this case i was trying USB storage devices.

So in order to see if the GUEST was properly set up for the use of USB devices, i plugged in a custom Microcontroller programmer ( a device for programming MICROCHIP PICS) which Ubuntu doesn't have a controller for... and success! the GUEST appears to recognize said USB device.

This leads me to believe we need to unbind the claim that our current distro has over our Mass storage USB devices in order to use them on the guest... I hope someone around here can give us a feed back!

---

