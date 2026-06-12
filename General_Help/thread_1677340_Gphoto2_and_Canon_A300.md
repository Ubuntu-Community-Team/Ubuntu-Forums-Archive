---
title: "Gphoto2 and Canon A300"
date: 2011-01-28
forum: General Help
---

### Post by Dsky on 2011-01-28
if i try this no problems

```
gphoto2 --capture-image-and-download --filename webcam.jpg

```

if i add this

```
gphoto2 --set-configure flashmode=0 --capture-image-and-download --filename webcam.jpg

```

the script freeze.... why?!

gphoto version 2.4.5

---

### Post by Dsky on 2011-01-28
typing  gphoto2 --list-config

i've this

> /main/settings/owner /main/settings/model
/main/settings/firmwareversion
/main/settings/time
/main/settings/synctime
/main/settings/output
/main/settings/orientation
/main/settings/capturetarget
/main/settings/capture
/main/imgsettings/canonimgquality
/main/imgsettings/canonimgformat
/main/imgsettings/canonimgsize
/main/imgsettings/iso
/main/imgsettings/whitebalance
/main/imgsettings/photoeffect
/main/capturesettings/zoom
/main/capturesettings/assistlight
/main/capturesettings/autorotation
/main/capturesettings/exposurecompensation
/main/capturesettings/canonflashmode
/main/capturesettings/shootingmode
/main/capturesettings/aperture
/main/capturesettings/focusingpoint
/main/capturesettings/shutterspeed
/main/capturesettings/meteringmode
/main/capturesettings/afdistance
/main/capturesettings/focuslock


so how to set the flash mode?

---

### Post by Dsky on 2011-01-28
i solved

> 
not  --set-configure flashmode=0
but  --set-config canonflashmode=0



---

