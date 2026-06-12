---
title: "Mounting USB In VirtualBox"
date: 2010-03-23
forum: General Help
---

### Post by chome4 on 2010-03-23
I've got GuestAdditions installed and can see the CD/DVD drive. How do you mount the USB so I can see my USB device?

---

### Post by darolu on 2010-03-23
The one you install from Ubuntu repositories does not have USB support.

Did you install Virtual Box from Sun's site/repos?

---

### Post by chome4 on 2010-03-23
> **darolu said:**
> The one you install from Ubuntu repositories does not have USB support.

Did you install Virtual Box from Sun's site/repos?

Can't remember. How can I check to see the origin my install?

---

### Post by howefield on 2010-03-23
Load up Synaptic Package Manager and search for virtualbox. If the one you installed has the term "ose" in the name, it is the repository version that doesn't have the ability to use USB devices.

---

### Post by chome4 on 2010-03-23
> **howefield said:**
> Load up Synaptic Package Manager and search for virtualbox. If the one you installed has the term "ose" in the name, it is the repository version that doesn't have the ability to use USB devices.

You're right! I've got the 'ose' one installed. There are seveal non-ose one referred to. Which one should I install?

---

### Post by linden940 on 2010-03-23
go this link....it will explain and there is a video you can watch

[http://www.youtube.com/watch?v=5SWzRVVzzAQ](http://www.youtube.com/watch?v=5SWzRVVzzAQ)

---

### Post by howefield on 2010-03-23
Go to this website and pick the version to suit your architecture and Ubuntu version. Download it and double click the file to start the install.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I'd uninstall the version you have first though, using Synaptic Package Manager. Don't worry if you have created a vm already, it won't be lost when you uninstall the ose version, the vdi file will still be there, you just need to recreate the vm settings and point it to the existing vm.

---

### Post by chome4 on 2010-03-23
Thanks for that. All Ok now.

---

### Post by monicamaria on 2010-04-09
Here are the steps that worked for me:

On the desktop:
 Menu System > Administration > Users and Groups
Click the keys to make changes, type password
Highlight you, the user, then click Properties
Under the "User Privileges" tab, scroll down and check the "Use Virtual Box" 
Click OK, then close.

Hope this helps.

Monica

---

