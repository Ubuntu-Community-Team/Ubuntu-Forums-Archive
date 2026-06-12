---
title: "Ipod Shuffle Mounting Problems"
date: 2010-09-04
forum: General Help
---

### Post by randyklein99 on 2010-09-04
I have a A1271 Ipod Shuffle that has been giving me fits. Whenever I plug it in, Ubuntu auto-mounts it to usb0 with root access only.  I can unmount it from there and then mount it to /media/Ipod, but don't want to do that every time and my wife won't want to do that even once. So how can I make this automatic?

---

### Post by randyklein99 on 2010-09-04
Update: After I plug it in, I run System>Administration>Disk Utility and see that it is mounted to /media/usb0.  If I click unmount, then mount again with that utility, it mounts it to /media/ipod.  Any clues on why it does that and/or how to make it just auto-mount to /media/ipod the first time?

Edit:  I've run Meerkat in VBox and this above problem doesn't occur.  It automounts to /media/ipod.  Of course, I don't know if that's Meerkat or VBox causing that.

Thanks.

---

### Post by randyklein99 on 2011-06-27
I think this problem got fixed when I was solving something else.  According to this [thread]("http://ubuntuforums.org/showthread.php?t=1469499"), I removed usbmount, pmount, and gnome-pilot.  Ipod is now recognized and works.

---

