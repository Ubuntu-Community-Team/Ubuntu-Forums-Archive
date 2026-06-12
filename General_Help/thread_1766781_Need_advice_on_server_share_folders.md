---
title: "Need advice on server share folders"
date: 2011-05-24
forum: General Help
---

### Post by lutubu on 2011-05-24
Hi guys

The server stuffs are new to me I need some advices please.


I intend to setup a Ubuntu file and printer server in my home. There are five users of mixed Windows and Ubuntu at our place so Samba seems to be a good choice. 


I intend to attach a USB portable hard drive as a share drive on the server, on this drive I want to set up:

- a place where I store movies, photos, and music anyone can access this place but can't delete/add files to it accept the administrator which is me. 

-I also want to set up five other private folders one for each user so they can store their stuff and the folders can only be accessed by their owner.


My question is should I just create six folders on the USB portable hard drive and assign access rights to each folder or should I partition the USB portable hard drive into six partitions and assign access right to each of the partitions? Or is their a better way of doing this?

Any advice appreciated

---

### Post by linuxinstalledfromhdd on 2011-05-24
You want to take your hard drive you have, and install it into a NAS external enclosure and hook it to your router with Ethernet cabling so you can have a file server. That way it is available over the network to any computer that wants to connect to it. 

As for the printer, that's easy. Just hook it to a desktop system that doesn't go anywhere... (if you have one) and usb to that system, and share it over the network to anyone that wants to install it.

---

### Post by btindie on 2011-05-24
If you create local user accounts on your server then when the users login via windows networking they will only be able to access their own 'home folder' share.

For the private one just edit the samba configuration file making it read only (possibly writeable by admin). You can always upload files to the server via NFS/SCP.

There's no need to create individual partitions, just the one is fine. Format it to ext4 and have it mounted on /home so when you add the users home directories they'll then be created on there. You can also create your public share on there - /home/public. Just add that path to your samba config.

If you can avoid using a USB drive then I would as it's much slower than SATA especially if you've got 5 users accessing movies/music...

---

### Post by linuxinstalledfromhdd on 2011-05-24
Gigabit router and a NAS gigabit enclosure works perfect. That's I've got going here.  Everything else I tried was choppy and intermediate at best, regardless of OS.  Just a tip if you are steaming anything like video.

---

### Post by lutubu on 2011-05-24
I am using an old laptop as a server for it less fan noise and low power  consumption, the printer I have is just a USB laser printer without  networking. I don't have choice of NAS or SATA I think I'll stick to  what I have for the time being. I'll mark btindie's post as the solution  I need.


I am really impressed of how quick and helpful people on this forum respond, surely I'll come back and bug you guys again :P. 


Cheers

---

### Post by linuxinstalledfromhdd on 2011-05-24
My suggestion was only for a optimal performance setup, if that can't happen, then of course whatever works is best.  :)

---

