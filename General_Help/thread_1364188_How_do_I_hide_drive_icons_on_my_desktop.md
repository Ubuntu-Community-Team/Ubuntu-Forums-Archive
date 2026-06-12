---
title: "How do I hide drive icons on my desktop?"
date: 2009-12-25
forum: General Help
---

### Post by 3pinner on 2009-12-25
I just created and formatted a partition on my HDD. When I boot the system, the hard drive mounts (which is what I want it to do) and shows up as an icon on the desktop.
How do I remove or hide drive icons from the desktop?

Thanks!

---

### Post by Ginsu543 on 2009-12-25
If you haven't already, download and install Ubuntu Tweak from [https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2). Under the Desktop --> Icons tab, there is an option to "Show mounted volumes on desktop" which you can click off. That should do what you want.

---

### Post by tom.swartz07 on 2009-12-25
> **3pinner said:**
> I just created and formatted a partition on my HDD. When I boot the system, the hard drive mounts (which is what I want it to do) and shows up as an icon on the desktop.
How do I remove or hide drive icons from the desktop?

Thanks!

As they say, "Google is your best friend!"

Here you go, from the How-to-geek
[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)


Merry Christmas!

---

### Post by doas777 on 2009-12-25
> **tom.swartz07 said:**
> as they say, "google is your best friend!"

here you go, from the how-to-geek
[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)


merry christmas!
+1

---

### Post by AlexDBall on 2009-12-25
Hi all, Merry Christmas!

you can also run gconf-editor.

navigate to apps/nautilus/desktop and uncheck the volumes_visible option

regards,

Alex

---

### Post by Morbius1 on 2009-12-25
The only problem with the gconf-editor method is that it also turns off the creation of a mount icon when when you insert a USB storage device. For people like me that need an extra reminder to unmount before disconnecting this is not a good thing ;-)

The only way around this is to automount the partition at start up and mount to a specific location:

Mount points in /home and /media will create a mount icon on the desktop. 

Mount points on "/" or /mnt will not. So if you have a "Data" partition mounted to /Data or /mnt/Data there will be no icon.

I guess it depends on how cluttered your desktop is whether you would notice a USB disk icon present or not.

---

### Post by AlexDBall on 2009-12-25
Yes, i think i'll agree with you Morbius1!

 I use the gconf-editor method just because i don't want anything on my desktop! :)
 Usually i unmount my usb drives/sticks from nautilus or the terminal.

---

### Post by AlexDBall on 2009-12-25
> **AlexDBall said:**
> Yes, i think i'll agree with you Morbius1!

 I use the gconf-editor method just because i don't want anything on my desktop! :)
 Usually i unmount my usb drives/sticks from nautilus or the terminal.

also i mount smb shares on login under my home directory using smbmount so i get another 6 icons only from that!

---

