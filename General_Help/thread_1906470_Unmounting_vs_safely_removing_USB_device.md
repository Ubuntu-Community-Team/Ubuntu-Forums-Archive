---
title: "Unmounting vs safely removing USB device"
date: 2012-01-09
forum: General Help
---

### Post by NautiusMaximus on 2012-01-09
I frequently plug my mp3 player into the USB port of my PC. When I want to unplug it again, I'm reluctant to just pull it out of the port without unmounting it or otherwise make it safe to remove first, and I figured that putting a brief script on my desktop that I could double-click to do this would be an easier thing to do than opening up my file explorer, navigating to the drive, and telling it to safely remove.

I have a couple of questions: does unmounting the device with umount make it safe to pull it out of the USB port? It doesn't seem to have quite the same effect as "safely remove", but maybe the differences aren't important?

And if the differences are important, is there a way I can achieve "safely remove" via a shell script?

Finally, my desktop contains not the script itself, but a shortcut to the script. When I double-click on the shortcut, it asks me if I want to run the script or edit it. Is there any way I can make it just go ahead and run it without asking me?

I'm using the default version of Ubuntu 11.10.

Many thanks
NM

---

### Post by MartijnNL on 2012-01-09
Unmounting (umount) should be enough.

You could replace the shortcut with a launcher which runs:

```
bash /path/to/your/script
```

---

### Post by NautiusMaximus on 2012-01-10
Thanks, the launcher trick was exactly what I needed.

Having said that, creating a launcher wasn't all that straightforward, so if anyone else is reading this thread and wants to do the same, [this link]("http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html") might be helpful. I followed the instructions on that page and they worked perfectly.

---

