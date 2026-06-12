---
title: "how do I enable virtualbox to use usb?"
date: 2011-05-17
forum: General Help
---

### Post by maddbaron on 2011-05-17
I am getting an error saying that my virtualbox has no access to my usb's but to enable access I need to add my user to the vboxusers ... how do i do that?

thanks in advance

---

### Post by papibe on 2011-05-17
If I remember correctly, you have install an extension in order to use USB ports. Take a look at this page: [VirtualBox Downloads]("http://www.virtualbox.org/wiki/Downloads").
Regards.

---

### Post by aeronutt on 2011-05-17
You have to use the non-free version from Sun, then you'll need to add your username to the 'vboxusers' group. Eg change /etc/group:

	vboxusers : x:124:
to
	vboxusers : x:124:<your user name>

Then,  in virtual box, under "Settings", then USB tab, add a USB filter to allow all USB devices.

At least, that's the way I did it. :)

---

### Post by silex89 on 2011-05-17
You have to download the guest additions package for the virtualbox (don't worry, you can download it from synaptic). Then you go to Menu-> Administration-> Users and Groups, go to advanced settings (it will ask you to authenticate) go to User Privileges and activate the "Use Virtualbox Solution" option.


Regards, good luck :D

---

### Post by maddbaron on 2011-05-17
> **papibe said:**
> If I remember correctly, you have install an extension in order to use USB ports. Take a look at this page: [VirtualBox Downloads]("http://www.virtualbox.org/wiki/Downloads").
Regards.

just did it and found how to enable user in vboxusers but the pop-up still happens, do i have to reboot myself for it to take affect?

---

### Post by maddbaron on 2011-05-17
no luck, i added the extension, i changed user groups... i'm using the non-free version... not sure what to do next... would the ose verison work?

---

### Post by silex89 on 2011-05-17
> **maddbaron said:**
> no luck, i added the extension, i changed user groups... i'm using the non-free version... not sure what to do next... would the ose verison work?


I'm sorry!, I forgot to say that! lol, what I told you was for the OSE version :)

---

### Post by maddbaron on 2011-05-17
rebooting the system seems to have fixed it. 

Thanks for the help

---

