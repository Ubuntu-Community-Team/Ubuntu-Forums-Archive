---
title: "HELP - Installing Google Earth on Ubuntu.?"
date: 2009-10-12
forum: General Help
---

### Post by dealrocker on 2009-10-12
Google Earth puts a planet's worth of imagery and other geographic information right on your desktop. Its one of my favorite pastime, Love to search new places. Well, I am new in ubuntu and want to install Google Earth for my computer which is running Ubuntu 8.10. I have already downloaded Google Earth from the internet and when I try to open, it says "Cannot find application to install this package". Just wondering is there any application to install Google Earth..?

---

### Post by MelDJ on 2009-10-12
add the medibuntu repo to your software sources. [http://www.medibuntu.org/](http://www.medibuntu.org/)
then go to synaptic and find for the google earth package and install it

---

### Post by khelben1979 on 2009-10-12
The problem is that the file isn't executable, so you need to fix this by doing this:
```
chmod 777 [path] [file]
```
to change directory to your path on your harddrive:
```
cd [path]
```
to execute the file and start the installer:
```
./GoogleEarthLinux.bin
```

---

### Post by shaon3343 on 2009-10-12
*you can visit this page: *
**[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)**

---

### Post by scouser73 on 2009-10-12
You should visit this site: [[COLOR="Red"]**How To Install Google Earth 5 On Ubuntu**[/COLOR]]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/")

---

### Post by philinux on 2009-10-12
> **MelDJ said:**
> add the medibuntu repo to your software sources. [http://www.medibuntu.org/](http://www.medibuntu.org/)
then go to synaptic and find for the google earth package and install it

+1 best way without a doubt.

---

### Post by johnpap on 2009-10-13
OK, so you install medibtuntu, no problem so far, open synaptic, find google earth and istall it... great.. done it with no prolems... and then what? where is it?... it's not any the applications menu, in facts I can't find it anywhere.... 
Is there something more to do ?

John

---

### Post by panvorax on 2009-11-08
> **johnpap said:**
> OK, so you install medibtuntu, no problem so far, open synaptic, find google earth and istall it... great.. done it with no prolems... and then what? where is it?... it's not any the applications menu, in facts I can't find it anywhere.... 
Is there something more to do ?

John

 I found the same problem. 
After following the advice in Scouser73's link to "How To Install Google Earth 5 On Ubuntu", I did not find the google earth icon in the Apps-internet-google earth location. Instead there was an icon on my desktop which I could use to activate google earth. 
 The software is not perfect though. The image jumps and flickers until it settles and can be viewed. If I move the image it flickers again for a few seconds and does that every time I adjust the map. Not Ideal but it warks sufficiently to use.

---

### Post by John Bean on 2009-11-08
> **panvorax said:**
> The software is not perfect though. The image jumps and flickers until it settles and can be viewed.
Sure software isn't perfect, but the software in question in this case is probably your video driver rather than Google Earth. 

I have similar issues (ATI chipset in my case) but only when Compiz is used as the window manager; I wrote a simple launch script to disable Compiz (if enabled), launch Google Earth then re-enable Compiz (if needed) it when it exits. No more flicker :-)

---

### Post by mörgæs on 2009-11-08
If the icons are not visible, try opening a terminal and write 

./googleearth 

in the home directory.

---

### Post by MelDJ on 2009-11-08
tried the medibuntu way?

---

### Post by mörgæs on 2009-11-08
It might also help to disable all visual desktop effects. Google Earth can be a memory hog.

---

