---
title: "Desktop Backgrounds"
date: 2010-01-09
forum: General Help
---

### Post by Quarkrad on 2010-01-09
I understand the pictures are in usr/share/backgrounds.  When you select a picture from the internet to be your desktop background (as I have) where does the physical picture go?  It does not go into usr/share/backgrounds - where is it?

---

### Post by Scunnered on 2010-01-09
If you save the item in the picture folder (places > home > picture) and follow on from there to system > preferences > appearance > background and select add.  This will let you select the saved item by highlighting it and clicking on open. You will not have the item in the backgrounds folder and on selecting it will let you display this on your desktop.

Hope this assists

---

### Post by t4ggs on 2010-01-09
i think it goes to /home/yourusername

---

### Post by warfacegod on 2010-01-09
In 9.10 it should go to the Downloads folder. Look in Places.

---

### Post by Quarkrad on 2010-01-09
Sorted - thank you all.

---

### Post by Bartender on 2010-01-09
Hey, I wanted to mention something I ran into the other day.  Downloaded a wallpaper.  Actually, it was just a high resolution picture that I figured might work, after some cropping and scaling, on a dual-monitor setup.  I downloaded it to the Desktop, then cropped/scaled it with GIMP, then sent it to the usr/share/backgrounds folder.  Something like this:

```
cd Desktop
sudo cp [COLOR="Blue"]picture.png[/COLOR] /usr/share/backgrounds 
```

Then went into Change Desktop Background, but couldn't place the file as wallpaper!!  I'd done this before several times, what was different?  Figured it out - something in the original file caused Ubuntu to give it limited permissions.

Instead of screwing around with "chown whatever" I just deleted the file and started over, but changed the permissions while the file was still at the desktop.  When I copied it to the backgrounds folder it worked like it was supposed to.

---

