---
title: "can I disable the built in camara"
date: 2009-12-04
forum: General Help
---

### Post by rastro123 on 2009-12-04
Hi does anyone know how to disable the inbuilt cam and use an external one instead on a laptop? Id really like to do this as then I can point the cam at whatever I like instead of trying to move the laptop around. Thanks if anyone can help.

---

### Post by khelben1979 on 2009-12-04
Have you looked in your BIOS settings? 

Other than that you can choose what video device you want to use in Skype. And [Skype]("http://en.wikipedia.org/wiki/Skype") can be used just as the [Cheese]("http://en.wikipedia.org/wiki/Cheese_%28software%29") application if you intend to only snap pictures.

---

### Post by HermanAB on 2009-12-04
Howdy,

I think you should just go ahead and plug the other camera in.  Every half decent application will allow you to choose the camera that you want to use.

---

### Post by rastro123 on 2009-12-04
Thanks guys, Im on the case.....

---

### Post by rastro123 on 2009-12-14
Iv tried both of the answers suggested here, but got nowhere. There is nothing in the bios, and I dont get the option of using another cam in the configuration of amsn (its there, but doesnt do anything) Anyone else have any help please??

---

### Post by khelben1979 on 2009-12-14
[Skype]("http://en.wikipedia.org/wiki/Skype") offers you the option of choosing your video device from the options menu. Have you tried this?

---

### Post by no2498 on 2009-12-14
open the terminal type gstreamer-properties
click video you can set the cam you like

---

### Post by rastro123 on 2009-12-18
Hi, thanks for reply. Im still getting nowhere fast though. I typed gstreamer-properties in and: 
boo@admin:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

I tried all the available options but nothing worked. Iv also tried skype but to no avail. Hp are hard work to contact and they are not interested in helping when I mention linux. Any other ideas? Im thinking to pull the inbuilt cam out and solder some wires to conect an external cam, but this is rather radical. Thanks.

---

### Post by khelben1979 on 2009-12-18
> **rastro123 said:**
> Iv also tried skype but to no avail.

What do you mean by this? In Skype you should be able to choose what video device that you yourself want to use.

---

### Post by rastro123 on 2009-12-19
Hi,well, I go into options in skype and click on select camera. but it only shows the hp inbuilt cam (/dev/video0)
Now, I have a windows partition also and I booted in windows, disabled the drivers for the cam and then installed the windows drivers for my external cam, went to messenger and it worked. So now Im thinking that this is what I have to do in linux, but not sure how to do it. - Disable the camera drivers and find some drivers for my ex-cam and install.....can it be that?

---

### Post by khelben1979 on 2009-12-19
By using the modprobe or insmod command with correct driver which matches your webcam, then you should see this device from within the Skype program.

---

