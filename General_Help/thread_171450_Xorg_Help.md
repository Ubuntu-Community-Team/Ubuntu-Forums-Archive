---
title: "Xorg Help"
date: 2006-05-06
forum: General Help
---

### Post by jonnyfive on 2006-05-06
I don't know anything about xorg (or too much about linux for that matter) but I found some information that will help me get this sis graphics card working but I don't understand exactly what to do

This one site says
"There is a "sis_drv.o" in /usr/X11R6/lib/modules/drivers, so I'd guess
> that's the driver to use. In fact, I quote from [http://www.X.org:](http://www.X.org:)
>
> 2.5 Video driver enhancements
>
> o SiS driver updates include
>
> o output device hotplugging
>
> o lots of fixes for 661, 741, 760 <<<<<<<----- HINT! HINT!
>
> o extended interface for SiSCtrl?
>
> o extended LCD handling (allow more modes)
>
> o HDTV support (480p, 480i, 720p. 1080i; 315/330 series)
>
> o Added video blitter Xv adapter (315/330 series)
>
> o extended RENDER acceleration"

Another says
"The installation scripts will recognize correctly the installed SIS video card. In any case the right driver to use in xorg configuration is "sis" with 1280x800@60 resolution for the wxga monitor. sis_agp module is loaded for Accelerated Graphic Port support."

How do I get to xorg configuration to set all this?

Please help me. Thank you.

---

### Post by rcarring on 2006-05-06
Drop to shell and type in as root 

dpkg-reconfigure xserver-xorg

then go thru the screens very very carefully

---

