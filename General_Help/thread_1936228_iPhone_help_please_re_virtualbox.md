---
title: "iPhone help please re virtualbox"
date: 2012-03-05
forum: General Help
---

### Post by mikee55 on 2012-03-05
Hi all, I'm connecting my daughters iPhone to my ubuntu machine using XP in Virtual box. However, I cannot connect to iTunes Store. The Virtual XP machine will connect to the Internet, I downloaded iTunes and installed it. I'm using a mobile broadband connection, and the iPhone won't connect to the store via this wifi mobile broadband connection. Would it be possible my bandwidth is the problem?

Thanks 
Mike

UK T-Mobile Wireless Pointer

---

### Post by sanderj on 2012-03-05
By default, the guest OS will not see a USB device. So, in your case, Windows (as guest) will not see the iPhone connected via USB.

Maybe [https://forums.virtualbox.org/viewtopic.php?f=7&t=35792](https://forums.virtualbox.org/viewtopic.php?f=7&t=35792) can help.

---

### Post by HiImTye on 2012-03-05
[Here]("https://help.ubuntu.com/community/VirtualBox/USB") are instructions for enabling USB in VirtualBox:
> For Oneiric Ocelot 11.10
Add yourself to the user group vboxusers, then log out and back in, to make use of available USB devices. To do this via the graphical interface, click System Settings/Users and Groups/Manage Groups.instructions for other versions of Ubuntu are there also

---

### Post by mikee55 on 2012-03-05
Virtual Box quite happily sees my usb ports. I use a wifi dongle to connect to my Wireless mobile broadband. I sycs the phone, and Internet explorer surfs the web!

Banshee doesn't work well, either!

Mike

---

### Post by HiImTye on 2012-03-05
I guess USB isnt your issue lol

sounds like you might have some ports blocked, if you are unable to connect via Banshee outside of VirtualBox, I would make sure that your router isn't blocking the necessary ports

edit: the easiest way to check is to make your machine a DMZ (allow all access to/from the internet) this is usually quite easy to find on most routers' firmware
edit2: right youre using a phone, it is likely that your phone provider blocks those ports required

---

### Post by mikee55 on 2012-03-05
I beg your pardon. I've added vbox to my user group thingys and I can connect.

Thank-you very much :) Still miffed that I have to have Microsoft on my Beautiful Ubuntu Natty Narwal 

Mike

---

### Post by HiImTye on 2012-03-05
I hear you, I have to use VBox for iTunes and AudioSurf and the CurseClient (but thankfully, nothing else)

---

