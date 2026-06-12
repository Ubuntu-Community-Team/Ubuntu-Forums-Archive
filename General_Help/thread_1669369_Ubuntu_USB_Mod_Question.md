---
title: "Ubuntu USB Mod Question"
date: 2011-01-17
forum: General Help
---

### Post by akurodam on 2011-01-17
I've recently created a usb boot up disk so i can run ubuntu on as many systems as i can while on the go instead of Windows. My only problem is i wanted to know if i could add a folder into the root of the usb and have my work saved there so that when i load i can access it but unfortunately the usb doesnt show up when loaded into the OS so i want to know if there are any work arounds.

All help is appreciated

Yours Sincerely 
Adam J Black

---

### Post by wilee-nilee on 2011-01-17
> **akurodam said:**
> I've recently created a usb boot up disk so i can run ubuntu on as many systems as i can while on the go instead of Windows. My only problem is i wanted to know if i could add a folder into the root of the usb and have my work saved there so that when i load i can access it but unfortunately the usb doesnt show up when loaded into the OS so i want to know if there are any work arounds.

All help is appreciated

Yours Sincerely 
Adam J Black

For a persistence load you will need to use the startup disc creator on a live ubuntu cd to load the ISO. I suggest a live Ubuntu cd not knowing if you have a actual Ubuntu install.

---

### Post by akurodam on 2011-01-17
> **wilee-nilee said:**
> For a persistence load you will need to use the startup disc creator on a live ubuntu cd to load the ISO. I suggest a live Ubuntu cd not knowing if you have a actual Ubuntu install.

I have both a live CD and USB drive both loaded with ubuntu. 
the usb drive by itself does boot ubuntu when plugged in
i simply want to know if i can somehow edit the files to allow me to access the USB files as the usb doesnt show up when 10.10 is booted

---

### Post by wilee-nilee on 2011-01-17
> **akurodam said:**
> I have both a live CD and USB drive both loaded with ubuntu. 
the usb drive by itself does boot ubuntu when plugged in
i simply want to know if i can somehow edit the files to allow me to access the USB files as the usb doesnt show up when 10.10 is booted

Do you think it might help to have the information such as how you loaded it? How big is the thumb?

If it is a unetbootin load no you can't adjust it to keep files.

---

### Post by akurodam on 2011-01-17
> **wilee-nilee said:**
> Do you think it might help to have the information such as how you loaded it? How big is the thumb?

If it is a unetbootin load no you can't adjust it to keep files.

i used the ubuntu ["website"]("http://www.ubuntu.com/desktop/get-ubuntu/download")  to create a bootable usb drive.
I dont know what you mean by thumb, a little rusty on linux tbh :-?

how would i find out if it is or not

---

### Post by t0p on 2011-01-17
> **akurodam said:**
> 
I dont know what you mean by thumb, a little rusty on linux tbh :-?

how would i find out if it is or not

By "thumb" he meant the usb stick you're using - ie, how large is the live usb stick?

I suppose he's asking that to ascertain whether or not you have enough "spare" space on the stick to save extra data on.

---

### Post by wilee-nilee on 2011-01-17
> **akurodam said:**
> i used the ubuntu ["website"]("http://www.ubuntu.com/desktop/get-ubuntu/download")  to create a bootable usb drive.
I dont know what you mean by thumb, a little rusty on linux tbh :-?

how would i find out if it is or not

I believe the installer used is the pendrive installer and if you wanted persistence it would be from it if possible. 

How big is the pendrive/thumbdrive/usbdrive---whatever you want to call it.

---

### Post by wilee-nilee on 2011-01-17
> **t0p said:**
> By "thumb" he meant the usb stick you're using - ie, how large is the live usb stick?

I suppose he's asking that to ascertain whether or not you have enough "spare" space on the stick to save extra data on.

Yes the size and the users toolset so we can get this set as they like it.

Op do you still have the original ISO downloaded?

---

### Post by C.S.Cameron on 2011-01-17
If, when booted from the drive you look in filesystem/cdrom you will find the actual files on the drive.
This folder is read only in 10.10 so you should do a gksu nautilus to access them.

---

### Post by wilee-nilee on 2011-01-17
> **C.S.Cameron said:**
> If, when booted from the drive you look in filesystem/cdrom you will find the actual files on the drive.
This folder is read only in 10.10 so you should do a gksu nautilus to access them.

I am going to let you take care of this. We do things differently, especially ascertaining whether the person being helped understands, and whether we are actually helping.;(

---

### Post by akurodam on 2011-01-17
> **wilee-nilee said:**
> I believe the installer used is the pendrive installer and if you wanted persistence it would be from it if possible. 

How big is the pendrive/thumbdrive/usbdrive---whatever you want to call it.

The USB drive is 4gig

---

### Post by akurodam on 2011-01-17
> **wilee-nilee said:**
> Yes the size and the users toolset so we can get this set as they like it.

Op do you still have the original ISO downloaded?

Indeed I do

---

### Post by akurodam on 2011-01-17
> **C.S.Cameron said:**
> If, when booted from the drive you look in filesystem/cdrom you will find the actual files on the drive.
This folder is read only in 10.10 so you should do a gksu nautilus to access them.

Would you mind explaining what a gksu nautilus is and how one would go about doing it

---

### Post by baddnady23 on 2011-01-17
Is this what your looking for?

[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

---

### Post by C.S.Cameron on 2011-01-17
Yo can either press Alt F2 and type gksu nautilus or open Terminal and type gksu nautilus.

Nautilus is like the Ubuntu equivalent of Windows Explorer.
gksu gives you super user privileges.

---

