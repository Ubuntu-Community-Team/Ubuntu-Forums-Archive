---
title: "Want to make a File Server."
date: 2010-03-03
forum: General Help
---

### Post by Crumbs744 on 2010-03-03
Hi everyone, 

Thanks in advance for the expert help.

I wasn't sure if i should have posted this in the absolute beginners section...

I started to collect the bits for putting together a file server, originally i was going to go for a windows OS since i was familiar but the i thought i may as well play around a bit with ubuntu server.

So i grabbed the 9.10 server ISO, install it onto my 4GB CF card i have plugged into the IDE port via a converter.

Seems to install fine and i got samba up and running and so far thats about all.

I want to get some kind of DC++ client working on it as well, im not sure if i need some kind of GUI for it...

Any suggestions would be greatly appreciated! 

thanks

---

### Post by gsmanners on 2010-03-03
I think the highest rated DC client for Linux is linuxdcpp, which has a GUI. I don't know anything else about it, as I've never used anything like that.

See [http://linuxdcpp.berlios.de/](http://linuxdcpp.berlios.de/) for more details.

---

### Post by Crumbs744 on 2010-03-03
does that mean i have to have some kind of gui installed like gnome or kde?

Or will the linuxdcpp gui run indepently


Other things i should have mentioned:

I needs to run about 4 SATA HDD's in RAID 5 and be able to expand that array later on, up to about 10 HDD's

---

### Post by gsmanners on 2010-03-03
That app uses GTK, so your best bet would be Xfce or at least LXDE.

I don't know much about RAID. I think that's mostly handled in hardware or in the kernel at this point.

---

