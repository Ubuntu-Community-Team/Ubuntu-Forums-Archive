---
title: "Virtual Box and USB access"
date: 2011-07-07
forum: General Help
---

### Post by liquidmonkey on 2011-07-07
i'm running a win7 x64 laptop that has Ubuntu 10.10 with the latest version of Virtual Box.

is it possible for me access a USB stick that i plug into the laptop FROM WITHIN the VB ubuntu?

at the moment i can't see it come up anywhere but i could easily be missing where to look.

any ideas?
or maybe this is just a limitation with VB?


thanks in advance!

---

### Post by seawolf167 on 2011-07-07
I'd check a couple things:

[LIST]
[*]do you have the guest additions installed? (shouldn't have anything to do with it, but you should install it anyways)
[*]do you have USB Controller support enabled in the settings menu?
[*]do you have USB 2.0 support (ECHI) enabled in the settings menu?
[/LIST]

Note that you cannot access the settings menu if the virtual OS is running.

---

### Post by haqking on 2011-07-07
There is the VB additions as well as the VB extensions pack which is available from the site which offer further USB support.

You need to enable USB support from the settings and also someimtes may need to go to devices menu and tick the item to mount it within the VM itself.

---

### Post by wkulecz on 2011-07-07
Unless something has changed recently, the version of Virtual Box in the Ubuntu repos doesn't support USB,  You need to get the version direct from the Oracle Virtual Box web site, where they have sample apt-get commands and a sources line to use their repo.

---

### Post by liquidmonkey on 2011-07-07
VB additions - check
USB controller - check
ECHI - check
VB extension pack - check

there is a small icon in the bottom right of the ubuntu window which indicates USB activity (third icon from the left) and if i right click this, any attached USB stuff comes up.

i can access the USB2.0 sticks BUT anything attached to my laptops USB3.0 port does not work. its shows, but simply gives an error when trying to read it.

but i was able to access a USB3.0 mem stick which is cool.

so the USB sticks don't come up automatically when plugged in but i can access them by using the usb icon in the bottom right.

thanks for the help!

---

### Post by howefield on 2011-07-07
The process I go through (albeit Ubuntu host with Windows guest) is..

1. Install Virtualbox - Version 4.0.10 (from virtualbox.org)
2. Add user to vboxusers group. (prob not required in Windows host)
3. Install extension pack - (downloaded from virtualbox.org).
4. Load Windows VM and install guest additions.
5. Insert USB device, right click on the USB icon on VM window "taskbar" and select the USB device I want, which then loads the drivers ect in the guest.

This works for Ubuntu guests also.

---

