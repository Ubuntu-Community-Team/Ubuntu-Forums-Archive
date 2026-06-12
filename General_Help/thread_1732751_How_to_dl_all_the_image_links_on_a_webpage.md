---
title: "How to d/l all the image links on a webpage"
date: 2011-04-18
forum: General Help
---

### Post by davesmith on 2011-04-18
I am looking for a spider program for Ubuntu like Image Wolf was in Windows. With Image Wolf i could set it to dowload all the images on a webpage.

I like astronomy, and I want to get all the supernovae pics from this page:-

[http://www.astrosurf.com/snaude/sn2010.htm](http://www.astrosurf.com/snaude/sn2010.htm)

but dont have time to manually click the links one by one. Is there an Ubuntu application that would do it?

Thanks

---

### Post by TeoBigusGeekus on 2011-04-18
```
wget -r -A.jpg,.JPG http://www.astrosurf.com/snaude/sn2010.htm
```

---

### Post by davesmith on 2011-04-18
Thanks, it worked. That was cool code and I am much obliged. A lesson learned, i think!

DaveS:)

---

### Post by davesmith on 2011-04-25
Is there any way to restrict the size of jpg downloads with wget? I am realy only interested in jpgs with a minimum size of say, 250kb.

using 
[FONT=monospace]
[/FONT]wget -r -A.jpg,.JPG [http://www.astrosurf.com/snaude/sn2010.htm](http://www.astrosurf.com/snaude/sn2010.htm) 
downloads all the supernova thumbs too, and clogs up the destination directory....

Thanks

---

