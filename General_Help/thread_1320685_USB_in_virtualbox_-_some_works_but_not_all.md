---
title: "USB in virtualbox - some works but not all"
date: 2009-11-09
forum: General Help
---

### Post by blazemore on 2009-11-09
The screenshot should explain it all.

I have a weird problem whereby some USB devices work in Virtualbox, and some don't. I need the USB drive to appear in Windows, and for Windows to have direct access to the hardware (to format it and mark the partition as bootable) but Virtualbox won't even let me select it, although it passes my printer through fine.

OS: Linux Mint 7 (Jaunty Based)
Virtualbox: 3.0.10

EDIT: Yes I'm in the VBoxUser group (or whatever it's called)

---

### Post by jbrown96 on 2009-11-09
The drive wouldn't happen to be mounted in Ubuntu? Maybe it automounts. You may have to manually unmount to set up the filter in Virtualbox settings the first time.

---

### Post by blazemore on 2009-11-09
> **jbrown96 said:**
> The drive wouldn't happen to be mounted in Ubuntu? Maybe it automounts. You may have to manually unmount to set up the filter in Virtualbox settings the first time.

I've unmounted it but it still won't let me use it

---

### Post by wilee-nilee on 2009-11-09
Since you have some usb's working I assume you know how to add them to the usb list in the startup gui.

---

### Post by blazemore on 2009-11-09
I haven't done anything like that. It just worked.

---

### Post by t0p on 2009-11-09
> **wilee-nilee said:**
> Since you have some usb's working I assume you know how to add them to the usb list in the startup gui.

> **blazemore said:**
> I haven't done anything like that. It just worked.

I assume you were responding to wilee-nilee's post?  Well, that's odd.  The *usual* way to get a USB device to work is to go to **Devices > USB devices** and to check the device(s) you want to work.  Those devices will then (I think) be unmounted in the host OS and available to the guest OS.

This is from memory.  I don't have a VirtualBox handy right now.

---

### Post by jbrown96 on 2009-11-09
T0p's right. You need to create USB filters in Virtualbox. I figured you had already done this. Shut down the VM. Open the virtualbox control center. Select the VM and go to settings, USB should be an option at the bottom, and create filters for the devices you want. Now you should be able to access them in Virtualbox.

I think you were having problems because you need to create the filters while the VM is off.

---

### Post by wilee-nilee on 2009-11-09
> **t0p said:**
> I assume you were responding to wilee-nilee's post?  Well, that's odd.  The *usual* way to get a USB device to work is to go to **Devices > USB devices** and to check the device(s) you want to work.  Those devices will then (I think) be unmounted in the host OS and available to the guest OS.

This is from memory.  I don't have a VirtualBox handy right now.

You are correct sir, I haven't used a virtual for over a year but I knew what you describe is part of the main startup GUi, thanks for clarifying this. ;)

---

