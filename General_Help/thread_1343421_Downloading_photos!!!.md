---
title: "Downloading photos!!!"
date: 2009-12-01
forum: General Help
---

### Post by Himself2007 on 2009-12-01
Hello

I have a Canon A85 camera with some photos on it.
When I connect it on USB, Ubuntu mount the camera so...detected.
When I start F-Spot which is correctly configured with destination folders, it reports to be unable to connect to camera, that it also previously detected!
I tried "Camera" and "digikam"...no success.
What would you suggest?
Thanks.

Luc

---

### Post by audiomick on 2009-12-01
use the file manager to copy the photos onto your drive, and try importing them from there, or take the card out of the camera and put in your card reader if you have one. Mine is faster than the camera (pentax K10 D)

---

### Post by Himself2007 on 2009-12-01
New try with F-Spot, now with camera connected but unmounted afterwards.
So when I click to download photos there is a message (picture under...), after which I press "Skip".

[[IMG]http://img109.imageshack.us/img109/3774/screenshottj.png[/IMG]](http://img109.imageshack.us/i/screenshottj.png/)

This process repeats itself for each photo!
At the end all my photos appears in my downloaded photos folder.
How can I fix this? 
Thanks!

Luc

---

### Post by audiomick on 2009-12-01
sorry, no idea...:(

---

### Post by Himself2007 on 2009-12-01
> **audiomick said:**
> use the file manager to copy the photos onto your drive, and try importing them from there, or take the card out of the camera and put in your card reader if you have one. Mine is faster than the camera (pentax K10 D)

Audiomick

Rejected!!!
It's too easy to do.
It has to be complicated and done by a software!
Hey...just joking!
The reason I'd like to use a software is to have all photos downloaded and placed in a dedicated folder.
Some folders are named by date and some folders inside them contain panoramic pictures.
My actual canon "downloader" does it this way in XP and I love it.
But I realize actually that F-spot does not offers this downloading feature.
So I'm looking for a software that does it...and is download capable...without erratic behavior!

Luc

---

### Post by mechro on 2009-12-01
I have a similar problem when using digikam from Gnome.

My workaround is to **unmount** the camera when I've plugged it in and then fire up digikam. Digikam then auto detects the camera.

---

### Post by Himself2007 on 2009-12-01
Mechro

Does Digikam has a configurable way to download photos?
I mean...can it create dedicated named folders for placing photos into?

Luc

---

### Post by mechro on 2009-12-01
Well, when you import and download in digikam you can..

Download all or selected into any folder/album you choose.

or...

Download all or selected into any new albums you create.

---

### Post by Himself2007 on 2009-12-03
mechro

OK. I understand.
That's a way to do it and that may be fine for tou.
But I want  to end up with self-created folders showing the date of these photos. 
This is something I cannot do because I would have to open and watch these photos's Exifs and this is cumbersome for nothing.
This is something that the downloading part of the software should do by itself.
Do you understand my point?
Just looking for a downloading software that could do this task.
There should be one somewhere in Linux world for this.
My basic Canon software does it.

Luc

---

### Post by hatteras22 on 2009-12-03
Para conectar físicamente la cámara al pc se usa:

1-Un cable que se conecta por un lado a la cámara, y por el otro extremo al pc por usb.

2- Si utilizas la cámara digital con tarjeta de memoria externa puedes sacar la tarjeta (es recomendable hacerlo así si es posible) y leer la tarjeta de manera independiente, usando un lector de tarjetas, o un adaptador usb, y hacer lo indicado a continuación.

[http://hatteras.wordpress.com/2009/12/02/pasar-fotos-desde-la-camara-digital-al-pc/](http://hatteras.wordpress.com/2009/12/02/pasar-fotos-desde-la-camara-digital-al-pc/)
-----------------
To connect physically the camera to the PC: it(he,she) is used:

1-Un cable that connects on the one hand to the camera), and for another end to the PC for usb.

2-If you use the digital camera with card of external memory you can extract the card (it is advisable to make it like that if it is possible) and to read the card of an independent way, using a reader of cards, or an adapter usb, and to do the indicated later.



[http://hatteras.wordpress.com/2009/12/02/pasar-fotos-desde-la-camara-digital-al-pc/](http://hatteras.wordpress.com/2009/12/02/pasar-fotos-desde-la-camara-digital-al-pc/)

---

### Post by blur xc on 2009-12-03
Regardless of the platform, I've never had good consistent success letting some photo manager copy photos from my camera.  My suggestion- make a destination folder, and then copy/past or drag/drop the files manually.  Way more reliable and safer.  Then use F-Spot or whatever to do whatever else you want done w/ them.  

When using Lightroom in Windows, the import tool has the option to look at attached media for files to import, but then it says it can't ever find any pictures, so I'd have to do that manually too.  And that's a high end proprietary program.  When we first went digital year ago, out of ignorance we used the Kodak easy share software, and that we also next to useless.  

Take control and do it yourself.  I'm writing a shell script to do it.

BM

---

### Post by StuartN on 2009-12-03
> **Himself2007 said:**
> This process repeats itself for each photo!

I would try removing the spaces in "/home/luc/Album de photos/Downloaded photos" just in case the programmers do not expect spaces in paths.

---

