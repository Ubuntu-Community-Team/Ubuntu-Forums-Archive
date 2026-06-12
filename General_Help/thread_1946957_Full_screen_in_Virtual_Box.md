---
title: "Full screen in Virtual Box?"
date: 2012-03-25
forum: General Help
---

### Post by Spewed on 2012-03-25
I'm running Ubuntu 11.10, and I have windows XP professional in VirtualBox. The only problem that I have with it is the screen resolution. I'm wanting to use this primiarly for things like Netflix. How I tried adjusting the screen resolution and didn't get my native screen resolution, and it actually made things harder to view. 

How can I enter full screen mode with Virtual Box? I know there is a way to do it in VMware Workstation, what about Virtual Box?

---

### Post by Habitual on 2012-03-25
I fire up my WinTendo Vbox (for netflix also) and press F11.

Be sure to have installed the appropriate Extension Pack...

---

### Post by Spewed on 2012-03-25
> **Habitual said:**
> I fire up my WinTendo Vbox (for netflix also) and press F11.

Be sure to have installed the appropriate Extension Pack...



What extension pack? :P

---

### Post by Bobhuber on 2012-03-25
> **Spewed said:**
> What extension pack? :P
Virtualbox requires an extention pack for correct graphics and USB support.. Use the latest VB for your system located on the Oracle site along with the aforementioned extension pack.

---

### Post by uRock on 2012-03-25
The extension is called Guest Additions. When you have the VBox window open, click Device, then click Install Guest Additions. This should show an autorun prompt in Windows, if not, then it should show a guest additions CD image, which you can double click to open, then find the installer exe within the image.

---

### Post by Habitual on 2012-03-25
> **Spewed said:**
> What extension pack? :P

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by Spewed on 2012-03-25
> **Habitual said:**
> [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)


Okay, so I opened up Windows XP through Virtualbox and I clicked "Devices -Install Guest Additions". Here is the message that I get. 

Could not find the VirtualBox Guest Additions CD image file /usr/share/virtualbox/VBoxGuestAdditions.iso or /usr/lib/virtualbox/additions/VBoxGuestAdditions.iso.
Do you wish to download this CD image from the Internet?

I click on yes to download it from the Internet, and then get the following message.

Failed to download the VirtualBox Guest Additions CD image from [http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso).
Error downloading [http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso) - server replied: Not Found

-------------------------------------------------------------------------

After that I went to the link the previous poster provided above and downloaded Oracle_VM_VirtualBox_Extension_Pack-4.1.10-76795.vbox-extpack

I installed it, it installed in literal seconds, and still no full screen? I pressed f11, and nothing.

---

### Post by jerome1232 on 2012-03-25
Just click View -> Switch to full screen

---

