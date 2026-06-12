---
title: "Archos 5 insists on being MTP"
date: 2010-11-18
forum: General Help
---

### Post by fistoprince on 2010-11-18
Hey everyone

I got myself an Archos 5 and pretty much have it triple booted using OpenAOS ([http://www.openaos.org/](http://www.openaos.org/)) but the partition I added with FroYo that I wanted in particular won't boot up.

BUT

My real problem is when going into Archos mode and plugging it in to my Ubuntu laptop, it insists on being some strangely mounted thing 'MTP' or something. I can view the files and folders via Nautilus, but I can't copy them, move them or add to them. I need to open a file with gedit to set up a patch. Nope! Gedit says it's a 'gphoto2' type mount thing.

"Could not open the file gphoto2://[usb:002,006]/menu.lst."

I would not be surprised if Rythmbox set it up like this, I tried it because of the big button in Nautilus when I open the device. Oops...

Any help appreciated! I just need this thing mounted...

---

### Post by The Cog on 2010-11-18
Try killing the process gvfs-gphoto2-volume-monitor and then connect the Archos 5 (whatever that is).
**sudo killall gvfs-gphoto2-volume-monitor**
Just a wild guess.

---

### Post by JEDIDIAH on 2011-01-09
Go into the system menus and make sure the device is still set to present itself as storage device and hasn't reset itself to MTP for some reason. 

Mine got reset like that when I installed the Android Market on it.

---

