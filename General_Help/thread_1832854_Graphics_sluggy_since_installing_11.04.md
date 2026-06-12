---
title: "Graphics sluggy since installing 11.04"
date: 2011-08-25
forum: General Help
---

### Post by Apocalypse_666 on 2011-08-25
Dear everyone,

Ever since upgrading/installing (I've done both) the graphic performance of my machine has gone down drastically. Before the upgrade everything always ran smooth as butter, even with all possible effects enabled. However, ever since the upgrade, even simple things like scrolling or typing in my browser lag noticeably. Also, full screen playback of HD content now lags. 
Now, I've disabled the Sync to VBlank option under openGL in CCSM. This has helped quite a bit, but performance is still not the same as it used to be! I have an ATI HD 4290, which should be more than sufficient to run this kind of environment, amirite?! The proprietary driver is installed and running. 

Does anybody have a clue?!

My system:
AMD Phenom II X4 B50 (3.2 ghz quadcore)
4 GB RAM (3.6 for system, 0.4 used by GPU)
ATI HD 4290
ASRock 890GM Pro3 mobo

Ubuntu 11.04 (natty)
Kernel 2.6.38-11-generic

Thanks a lot! 

Linus

---

### Post by madjr on 2011-08-25
is either the graphics driver or something related to compiz.

have you tried login out and checking the performance in either ubuntu classic (gnome2 no effects) or in unity2d ?

also is a good idea to install new releases into new partitions, just in case there is a regression and you need to stick with your current for a while. I usually test for a week and move to that or i wait for the lts.

---

### Post by Apocalypse_666 on 2011-08-25
Yeah, and indeed, that does solve the lag. 
However, I'd like to try and fix it *with* effects, as Unity seems pretty rad! :)

Regards,

Linus

---

### Post by imortalninja161 on 2011-08-25
yer that is definitely sufficient GPU power for the GUI and i cant save i have the same issue on my laptop i only have Intel HD integrated graph. The main point to consider is natty is still pretty buggy. Also disablign unity could help But i doubt that is the issue. to make sure your Graphics some how have not been crippled download a program called MSI afterburn To insure your graphics card is set to max safe output like i should be.

Thanks
imortalninja

---

### Post by Apocalypse_666 on 2011-08-25
I'm pretty sure my card is set correctly on a hardware level, if that's what you're trying to say :). I have a dual boot setup with windows, which gives me no trouble at all. Also, I've just removed Fedora 15 from my system, which ran Gnome3 without a hitch. 
Thanks though!

---

### Post by madjr on 2011-08-25
> **Apocalypse_666 said:**
> I'm pretty sure my card is set correctly on a hardware level, if that's what you're trying to say :). I have a dual boot setup with windows, which gives me no trouble at all. Also, I've just removed Fedora 15 from my system, which ran Gnome3 without a hitch. 
Thanks though!

ok, i see.

it seems to be a compiz bug then.

not sure if you can really do too much about it, except wait for them to fix it in next release (you should start testing oneiric to see how is progressing with your hardware).

i've just tested both unity 3d and 2d in oneiric and i must say am impressed that 2d is on par with the 3d visually (99% there) but with better performance.

other than that i guess you can  try some more searching for your gf card and unity and see if anyone has any other tips...

---

### Post by seawolf167 on 2011-08-25
> **Apocalypse_666 said:**
> The proprietary driver is installed and running.

Did you install the driver from the manufacturer website or from "Additional Drivers"? And if you installed it from the manufacturer website, did you reinstall it after your upgrade?

---

### Post by Apocalypse_666 on 2011-08-25
I did it through the Additional Drivers. And, I have a fresh install right now, no update :)

---

### Post by seawolf167 on 2011-08-25
> **Apocalypse_666 said:**
> I did it through the Additional Drivers. And, I have a fresh install right now, no update :)

Ahh ok, nevermind then - I was thinking it could be a driver issue previously.

---

