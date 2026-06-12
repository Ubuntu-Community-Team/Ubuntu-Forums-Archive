---
title: "USB issues on Virtual Machines"
date: 2009-07-21
forum: General Help
---

### Post by St Nabi on 2009-07-21
Hi guys, 

I was just wondering if anyone knows how to connect USBs to virtual machines. I set one up on Ubuntu and it is running Windows Xp Professional on it perfectly. I would like to install additional things on the VM but the VM will not detect the USB.

Also anyone have any drivers for Saitek products that will be compatible with Ubuntu. I use a Saitek eclipse keyboard and Saitek/Cyborg mouse.

Cheers

St Nabi

---

### Post by cosine352 on 2009-07-21
If you are using virtual box you can just add /media directory as the shared folder.

---

### Post by St Nabi on 2009-07-21
Where can i add the media directory as a shared folder.

Sorry to sound ignorant...

---

### Post by cosine352 on 2009-07-22
I have attached a picture

1) click 'settings'
2) go to 'shared folders'
3) click add button
4) chose the path to share. For most external hard drives the mount point is '/media'

---

### Post by St Nabi on 2009-07-25
Hi, I got your screenshot and followed the instructions and after mentioning the folder path as media I have to give a folder name toadd share, it won't accept. I can't ok it and as a result it won't add it on to the vm...

---

### Post by jdeppel on 2009-07-25
If you're using the OSE version of VirtualBox (the one in the repos), it currently does not have USB support. 

If you would like USB support, head over to virtualbox.org and download the .deb package for the closed-source edition.

---

### Post by St Nabi on 2009-07-25
Hi there, 

Will that be the following link:-


[LIST]
[*]**VirtualBox 3.0.2 for Windows hosts** [x86/amd64]("http://download.virtualbox.org/virtualbox/3.0.2/VirtualBox-3.0.2-49928-Win.exe")
[/LIST]
St Nabi

---

### Post by jdeppel on 2009-07-25
No. Whichever OS you're installing VirtualBox on is the host. You'll need to follow the link for VirtualBox 3.0.2 for Linux hosts, then click on Ubuntu and then select the file for the version of Ubuntu you're running as well as the architecture (i386/x64).

Hope that helps.

---

### Post by Yvan300 on 2009-07-25
Just download the closed source version and then follow the link below for the usb support:
[http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host](http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host)

Oh and it would be a wise decision to grasp the file sharing options in virtual box, they will come in handy in the future.

---

### Post by St Nabi on 2009-07-25
Thanks people. 

I am going to try out the suggestions and will let you know how they went.

Regards

---

