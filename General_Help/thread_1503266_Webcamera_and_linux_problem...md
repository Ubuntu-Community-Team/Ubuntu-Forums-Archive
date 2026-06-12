---
title: "Webcamera and linux problem.."
date: 2010-06-06
forum: General Help
---

### Post by noveevon on 2010-06-06
anyone know how i can get my old [logitech quickcam stx communicate ]("http://i00.twenga.com/computers/webcam/logitech-quickcam-communicate-stx-p_81524vb.png")to work in linux?

ive tried most of the chat clients (skype, kopete, etc), and at the moment i am using emesene, from my side i can see myself using the webcam, but the other person only see a blank screen..

ive been online looking and so far without much luck...

also i tried using VMware, but every time i enable the webcam in the right side corner of the VMware screen my system freeze and i have to manually reboot..

in advance thank you!

---

### Post by davidmohammed on 2010-06-06
have you tried starting your client with something like

"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"

maybe using [webcams with skype]("https://wiki.ubuntu.com/SkypeWebCams") will help

---

### Post by noveevon on 2010-06-07
> **davidmohammed said:**
> have you tried starting your client with something like

"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"

maybe using [webcams with skype]("https://wiki.ubuntu.com/SkypeWebCams") will help


when i try this i get:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


i tried using webcams with skype, but all the versions of skype i tried crash at some time during the start up after installing in wine...ive tried from skype 2.0 upto 5.0 beta.. and now i am having a big problem uinstaling the various versions from my wine directory, they just dont seem to want to leave.. ive even deleted the various folders and also tried using ccleanr...

thanks for the help nonetheless..

---

### Post by davidmohammed on 2010-06-07
... I didn't know you can run skype from wine.

I use linux skype - have a look in synaptic manager and install skype from there.

You can clean up a wine installation by deleting the hidden folder .wine.  I think there is a way to show hidden files in the nauticus file manager.  Try deleting from there.

**Remember deleting .wine will erase any windows programmes you may have installed and therefore you will need to install again.**

If you are confident use a terminal session and type

rm -rf ~/.wine **** BUT DONT do that if you don't know what that does.****

You can delete the wine menu shortcuts by editing your menu.

---

### Post by noveevon on 2010-06-07
> **davidmohammed said:**
> ... I didn't know you can run skype from wine.

I use linux skype - have a look in synaptic manager and install skype from there.

You can clean up a wine installation by deleting the hidden folder .wine.  I think there is a way to show hidden files in the nauticus file manager.  Try deleting from there.

**Remember deleting .wine will erase any windows programmes you may have installed and therefore you will need to install again.**

If you are confident use a terminal session and type

rm -rf ~/.wine **** BUT DONT do that if you don't know what that does.****

You can delete the wine menu shortcuts by editing your menu.


ive been using the linux skype found on skype.com v 2.1.0.81-1 and still it dose not work... :(


thank you for the wine tips, sadly i have some programs installed that i do not wish to loose so i will just keep it status quo for now..

---

### Post by no2498 on 2010-06-07
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

in/on 910 and up cheese webcam booth is/should be loaded
look for it in sound & video

try the cam in cheese first


hope this helps

---

### Post by noveevon on 2010-06-07
> **no2498 said:**
> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

in/on 910 and up cheese webcam booth is/should be loaded
look for it in sound & video

try the cam in cheese first


hope this helps


my cam works in chesse etc, but not in skype...so it seems it works on my end, but not the other...

---

### Post by noveevon on 2010-06-09
bump..

---

### Post by derklempner on 2010-06-09
> **noveevon said:**
> when i try this i get:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Okay, make a bash script with the following:
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
You might not need the third line (except for the "skype" command), so see if that'll work for you.

---

