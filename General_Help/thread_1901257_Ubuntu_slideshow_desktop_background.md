---
title: "Ubuntu slideshow desktop background"
date: 2011-12-28
forum: General Help
---

### Post by bbno3 on 2011-12-28
I have a couple of pictures in a save folder on my computer.
I would like to create a background slideshow of these pictures *changes evey 15 minutes*
How will i go about doing this. Explain it in the simplest terms please.

---

### Post by West201 on 2011-12-28
Which version of Ubuntu are you running ? Are you using Gnome or KDE ?

---

### Post by sepo on 2011-12-28
You can set a background slideshow pointing to an XML file with all the pictures infos, instead of pointing to a single image.

Here's a sample:
```

<background>
  <starttime><year>2011</year><month>12</month><day>28</day><hour>00</hour><minute>00</minute><second>00</second></starttime>

  <static><duration>1700</duration><file>/home/sepo/mywallpaper/img1.jpg</file></static>
  <transition><duration>5</duration><from>/home/sepo/mywallpaper/img1.jpg</from><to>/home/sepo/mywallpaper/img2.jpg</to></transition>

  <static><duration>1700</duration><file>/home/sepo/mywallpaper/img2.jpg</file></static>
  <transition><duration>5</duration><from>/home/sepo/mywallpaper/img2.jpg</from><to>/home/sepo/mywallpaper/img3.jpg</to></transition>
</background>

```That file can be in /home/sepo/mywallpaper/mywallpaper.xml.

You can build it manually or use a program that generates it (I actually made and use a python script to do that; dunno if exists something more 'official' :) )
Remember: duration is in seconds, so 15 minutes is 900.

---

### Post by bbno3 on 2011-12-28
i AM running the latest ubuntu*non beta* oneric.
How will i put all my images into an xmi file?
what is that code and how can it change it to work on mine.

---

