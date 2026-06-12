---
title: "Help and opinions on Virtual NAS."
date: 2012-08-28
forum: General Help
---

### Post by eddie3000 on 2012-08-28
Hi there! After seeing how pricey dedicated NAS servers are I decided to try and make a virtual NAS in my computer. I don't require a NAS at home being turned on 24hours a day.
I have installed Ubuntu 12.04 (with gnome shell) as the host, and freenas as the host in virtualbox (version 4.1.12). I still haven't got it working. 
I have messed with virtualbox and managed to use the usb filter in the past with success using Winxp as the guest and various usb 2.0 devices. But I can't get virtualbox to recognize a usb external 2TB HDD I wish to use exclusively for freenas. Anybody know why I can't? Virtualbox won't even list the HDD for use with the guest OS. But the disk does work with the host. I have tried unmounting, but still won't show in virtualbox.
Is it a good idea to use freenas and virtualbox as a NAS?  Do I need an extra lan card exclusively for freenas? The computer I have is an AMD Athlon 4x 640 and 2GB of ram. I think it should be capable.
Thanks!

---

### Post by Lars Noodén on 2012-08-28
FreeNAS has gotten quite heavy of late, at least according to an [interview on FreeNAS](http://twit.tv/show/floss-weekly/198) I listened to.  

All the services in FreeNAS can be added to Ubuntu.  I'm not sure why you would need or want VirtualBox instead of running directly in the host.  Virtualizing adds a lot of overhead so you'll get better performance running normally.  Unlike some other system, Linux is designed to run a lot of services simultaneously so it's fairly easy and safe to add them in as needed.  I'd recommend just plain Ubuntu (or Debian) and then adding in the service(s) you want.  The result will be much lighter.  Probably the only two that you might find of interest would be SSHFS and/or Samba.

---

### Post by eddie3000 on 2012-08-28
Does anyone else think the same as Lars Noodén? He has already started to put me off the idea.
Thanks Lars for your reply.

---

### Post by Cheesemill on 2012-08-28
+1 for Lars.

I don't really see any advantages to running FreeNAS in a VM, only added complexity and overheads.

---

### Post by eddie3000 on 2012-08-28
Thanks. 
OK. 
I will completely ditch the idea. 
Cheers!

---

### Post by mastablasta on 2012-08-28
> **eddie3000 said:**
> Does anyone else think the same as Lars Noodén? He has already started to put me off the idea.
Thanks Lars for your reply.
 
yup. linux desktop is preety much server with desktop installed minus a few services. now these services can easilly be installed via software center or synaptics.
 
now to return to your questions you need guest additions for USB support. i am not sure if they alos support USB hard drives. 
but just scrap your crazy idea :-)
 
it's much easier & faster to just use your computer and add the services you want/need to it.
 
btw if oyu plan on buying a NAS or make one yourself, aside from freenas there is also openmediavault (debian based). a few things are a bit different but overall i read it is very stable and also easy to manage.

---

### Post by eddie3000 on 2012-08-28
Thank you very much for your suggestions. I will make a dedicated NAS when I can spare a few €. I might consider openmediavault then. Cheers!

---

### Post by Lars Noodén on 2012-08-28
You can still use the equipment that you have now to set up a NAS.  A NAS is just some file sharing services and it's easy to add or remove services from Linux.  You can run it on your current machine now and then move it over to new hardware when you do get it.

---

### Post by eddie3000 on 2012-08-29
Hi again.
I'm trying to get my NAS working. I am still quite a novice with linux and all other related stuff. So if I seem to be doing something wrong please tell me I'm an idiot for whatever reason ;-)
I want to be able to access the shared folder from all my computers. I have three plus the one that has all my files. I want to only grant access to my computers, and nobody else.
I have installed samba on all machines. I have tried creating a samba share with success, but everybody can see my files, not a good thing.
I am reading lots of confusing information on the internet about users, passwords, groups, permissions, directory masks, securtiy = ????, etc..... Who is nobody anyway (guest account = nobody)??
I have too many questions to post here. Can somebody show me a smd.conf file or some tutorial that does what I want?
Thanks.

---

