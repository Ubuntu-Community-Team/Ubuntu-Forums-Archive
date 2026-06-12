---
title: "Bash/script to convert dynamically generated image to jpg?"
date: 2010-06-09
forum: General Help
---

### Post by tarahmarie on 2010-06-09
Hi!

So, I have this awesome idea whereby I will, every few minutes, dynamically generate a nightside view of the earth.

Look here: [http://www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=](http://www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=)

That's the Fourmilabs sat image.  I want to set it as my wallpaper. I have already written the bash script to download it and drop it into my wallpaper directory, and I'm using kcron to update my wallpaper.  

Here's my problem. That URL yields an image, but I can't figure out how to convert that image to a usable file format. It's OTF generated, so unlike other sites that have a format like .../image.jpg, this URL isn't playing nice. 

Any ideas?

---

### Post by amite on 2010-06-09
Though i am not confirm will it work with ur pic's file format or not,and since i am not on my linux system now so can't be confirmed....but just give a try.
install imagemagick and then use
$convert  oldpic.format newpic.format

---

### Post by tarahmarie on 2010-06-09
While ImageMagick doesn't work, GIMP does.

However, I need to be able to open this URL from the CL, not in a GUI.  I get an error about 'nbsp not defined' when I try to do $gimp [http://www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=](http://www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=)

though using the Open Location command within the GIMP gui works fine.  How can I replicate that Open Location command at the CL?

---

### Post by tgalati4 on 2010-06-09
man curl
man xsetroot

The image gets cached in your .mozilla/firefox/xxxx.default directory.  It's standard jpeg.  I'm not sure what format you need?

---

### Post by tarahmarie on 2010-06-09
I appreciate the suggestion, but I have already scripted the image retrieval and wallpaper changing. 

My problem is one of image conversion, and as such, isn't addressed by a retrieval protocol or instructions on changing X backgrounds.

My problem is that Gimp opens that location perfectly fine from teh GUI, but not the CL. Does anyone know the bash for that "Open Location" dialog? Google tells me that it's deprecated, but that seems ridiculous to me.

---

### Post by tarahmarie on 2010-06-09
I've moved this discussion over to Multimedia...this is an image conversion problem.

---

### Post by alphacrucis2 on 2010-06-09
> **tarahmarie said:**
> I appreciate the suggestion, but I have already scripted the image retrieval and wallpaper changing. 

My problem is one of image conversion, and as such, isn't addressed by a retrieval protocol or instructions on changing X backgrounds.

My problem is that Gimp opens that location perfectly fine from teh GUI, but not the CL. Does anyone know the bash for that "Open Location" dialog? Google tells me that it's deprecated, but that seems ridiculous to me.

Why convert it? It's already a compliant jpg image.

---

### Post by tarahmarie on 2010-06-09
I'm aware that it's already a compliant image; I simply don't know how to SAVE it as one.  wget saves it as an .evif file, not a jpg.

---

### Post by alphacrucis2 on 2010-06-09
> **tarahmarie said:**
> I'm aware that it's already a compliant image; I simply don't know how to SAVE it as one.  wget saves it as an .evif file, not a jpg.


I tried it myself. The evif file doesn't contain the image. Open it in gedit and have a look. It's just text html so no conversion is of any use. Maybe when you do it via WGET, a script which would normally run in the browser to get the actual image doesn't run.

Edit. I think I have figured it out. wget (or rather bash) is breaking off at the first "&" in the url. Try putting quotes around it like this:

```
wget -A jpg "www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd="
```

The only thing is you will need to rename the file as something sensible.

---

### Post by tarahmarie on 2010-06-09
Thanks, Alpha!  Here's what I did in my script:

#!/bin/bash
wget -A earth.jpg "www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd="
mv /home/tarahmarie/Earth\?img\=learth.evif\&imgsize\=600\&dynimg\=y\&opt\=-n\&lat\=\&lon\=\&alt\=\&tle\=\&date\=0\&utc\=\&jd\= /home/tarahmarie/Pictures/Wallpaper/Dynamic/earth.jpg

Then, I changed my desktop settings to slideshow with a 1 minute checker for a new image and set the directory to .../Dynamic/

Now, it grabs the images and updates each minute!

Thanks!

---

