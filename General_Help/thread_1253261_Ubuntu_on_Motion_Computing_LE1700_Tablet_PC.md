---
title: "Ubuntu on Motion Computing LE1700 Tablet PC?"
date: 2009-08-29
forum: General Help
---

### Post by LoneWolfJack on 2009-08-29
Does anyone have ubuntu running on this machine (or any other tablet PC) with the OCR stuff?

I really need a new tablet PC and would prefer one I can use a lightweight ubuntu on.

Any thoughts?

---

### Post by Favux on 2009-08-29
Hi LoneWolfJack,

A lot of folks have Ubuntu working on tablet pc's, including Motion's.  I don't know what you mean by "OCR stuff".

---

### Post by LoneWolfJack on 2009-08-30
Optical character recognition

last time I tried using ubuntu on my LE1600 I couldn't get the touchscreen to work at all... and a tablet PC without being able to use the touchscreen and OCR is rather pointless. :)

---

### Post by Favux on 2009-08-30
Hi LoneWolfJack,

Well sure, but you can get the touchscreen working.  I'm not sure about the 1700, but the 1600 on down work.

[http://ubuntuforums.org/showthread.php?t=1061660&highlight=motion](http://ubuntuforums.org/showthread.php?t=1061660&highlight=motion)

[http://ubuntuforums.org/showthread.php?t=796359&highlight=motion](http://ubuntuforums.org/showthread.php?t=796359&highlight=motion)

[http://ubuntuforums.org/showthread.php?t=830496&highlight=motion](http://ubuntuforums.org/showthread.php?t=830496&highlight=motion)

Do you know if the 1700LE is still a serial Wacom tablet like the others or is it a usb?  It depends on what version of Ubuntu you are planning on installing as to how you set up linuxwacom to get the Wacom tablet stuff working.

With OCR I was asking are you talking OneNote or what?  There isn't a hand writing to text conversion in Linux.  CellWriter has letter to text conversion.  Xournal (and others) is like Journal, and you can take notes in it and annotate PDF's and such.

Evernote did have an online linux writing to text demo, but I think they discontinued it.

---

### Post by LoneWolfJack on 2009-08-30
Looks like linux has still a long way to go in terms of software/divers for tablet PCs. I guess I will just have to buy this thing and dual boot vista until I'm sure ubuntu is up to the task.

as far as the wacom, no idea what they use, sorry.

thanks for your help though.

---

### Post by Favux on 2009-08-30
Hi LoneWolfJack,

What I'm asking you is the internal connection to the built in Wacom tablet serial (like the previous Motion Computing models) or now usb?  Either way you should be able to get the Wacom tablet to work and be able to use your stylus and eraser in Gimp or Inkscape or Xournal or CellWriter, etc.

---

### Post by lazychris2000 on 2009-11-20
I stumbled across this posting and even though it is a bit old, I am going to share incase you are still looking for information. I work for a computer repair company and have a LE1700 in my possession, which was brought in by a customer.  I just fixed the power jack and it seems the harddrive is failing, but I digress...I booted off a live usb for ubuntu karmic (9.10) to backup the data and everything appears to be working except the screen.  I currently have it plugged into an external display, which works out of the box, and the touchscreen works (also out of box).  It is a little difficult to use because you have to look at the external screen and use the stylus on the embedded screen.  I have only been playing around with it for an hour or so while the harddrive backs up and have not found a fix for this, but it seems to be a pretty solid system with karmic. I had this problem with my old latitude C840 and I used to have to add Option "UseDisplayDevice" "DFP" to xorg.conf, but that does not work in this case--both screens display nothing.  I will only have this machine for another day or so, so I may not be able to play around with it long enough to find a fix, but if I do find one, I will let you know.
Interesting note to remember, the button on the stylus for right click is actually a middle click (like if you click the mouse wheel or hit left and right mouse buttons at the same time).  

Favux, I am not sure if it is a usb or serial touchscreen, but I attached several informational files which may be helpful (lshw, lspci, lsmod, etc)

Lonewolfjack, don't give up on ubuntu just yet.  There are a few kinks to work out, but I would imagine if you can get the screen to work, you would be set.

---

### Post by Favux on 2009-11-20
Hi lazychris2000,

Sounds like a fun project.

It looks like it is also a serial tablet pc because there's nothing in lsusb for a tablet.

You should be able to set it up following the links above.  I've got a couple more if you need them.

The video problem might be the onboard Intel:
```
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```
(or use "lspci | grep VGA").  There were problems with Intel on Jaunty and while Karmic fixed most of them...  So check the now closed Karmic forum.  Or search the rest of the forum with the above keywords.

One word of warning.  There appears to be a problem with serial tablets on 64-bit Karmic, but 32-bit is apparently OK.

---

