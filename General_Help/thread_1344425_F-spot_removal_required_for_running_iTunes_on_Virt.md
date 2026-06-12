---
title: "F-spot removal required for running iTunes on Virtualbox!!!??"
date: 2009-12-02
forum: General Help
---

### Post by smartsmokey on 2009-12-02
hi everyone - long time no post.Sorry I haven't been around to help you other Ubuntu pioneers. Hope all is well. 
Okay here's my problem - 
only way for me to run iTunes/my iPod is via running Virtualbox which I've installed Windoze Xpoop on. If F-spot is not on my Ubuntu (host OS), there's no problems when I run itunes in Virtualbox/plug in the iPod/sync. However, if F-spot IS installed, it basically crashes both the virtual OS and my host - f-spot opens up as soon as the ipod is detected - but not from Windoze of course - but from Ubuntu. So, it's like 2 systems accessing the ipod at the same time, and it just blows up. 
Only solution I have is to remove F-spot from Ubuntu before plugging in the ipod/starting Virtualbox...and this works perfectly. But of course if I try this with F-spot still installed the whole thing blows. 
So, I have to re-install F-spot whenever I want to load my iPod/run Vbox, and remove F-spot when I'm done, so pic uploads from an SD via printer will work correctly in Ubuntu. 
I love ubuntu and will never go back to "THEM" or "IT"...but if there was something I could do in order to stop myself from having to install and remove F-spot everytime I have to sync my ipod or upoload pics into Ubuntu via an SD card and my printer, it would really help. Any ideas guys/gals?
Thanks, smartsmokey

---

### Post by smartsmokey on 2009-12-02
bump?

---

### Post by howefield on 2009-12-03
Try going to Places > Home > Edit > Preferences and change as required in the media tab to stop F-spot trying to grab the ipod when you plug it in. ?

---

### Post by zaphod777 on 2009-12-03
try removing fspot and installing rythembox. I had to install rythem box before my other software would detect the ipod.

---

### Post by mike555 on 2009-12-03
You could just install " Camera" program, it lets you get photos from your camera or card ........ without f-spot.

---

### Post by zaphod777 on 2009-12-03
> **mike555 said:**
> You could just install " Camera" program, it lets you get photos from your camera or card ........ without f-spot.

Thats not the OP problem. 

He needs fstop pr he can't use itunes with his ipod in a VM.

---

### Post by 3rdalbum on 2009-12-03
It doesn't look like there's anything in the F-spot package that's forcing itself to be opened when you plug in a device, so maybe Gnome is opening F-spot when you insert the iPod. I can't remember the name of the program that lets you set this (I'm not in Gnome, sorry) but it definitely exists.

---

### Post by The Cog on 2009-12-03
There was an issue a while ago with gphoto2 grabbing cameras and blocking other access to them. Don't know if it's solved recently, but try this command and see if it helps:

sudo killall gvfs-gphoto2-volume-monitor

I'm not sure if there's any connection between gphoto and f-spot, so I have to admit I'm fishing here, but it's worth a shot.

---

### Post by StuartN on 2009-12-03
> **The Cog said:**
> There was an issue a while ago with gphoto2 grabbing cameras and blocking other access to them. Don't know if it's solved recently,

Apparently not, this was posted today [http://www.ausimage.us/Blog/20091202](http://www.ausimage.us/Blog/20091202)

Personally, I would nuke iTunes if it was crashing my applications.

---

