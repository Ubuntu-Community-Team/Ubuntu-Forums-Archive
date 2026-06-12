---
title: "unable to watch movies without lagging"
date: 2011-05-27
forum: General Help
---

### Post by ddimit on 2011-05-27
i have tried 100 ways for being able to watch movies without lagging but nothing
so im moving to windows

---

### Post by Rebelli0us on 2011-05-27
Have you tried the XBMC Media Center? It's the only way to play commercial movies on my ubuntu machines. You can always dual boot, linux does some things better than windows, especially the price.

---

### Post by LordNeo on 2011-05-27
gl

---

### Post by Joe of loath on 2011-05-27
OP, do what you want. All we can do is offer suggestions and help ;) Sure it's a CPU speed or graphics card driver issue?

---

### Post by davidvandoren on 2011-05-27
Install ubuntu 10.04
Then **System** / **Administration** / **Hardware drivers**   check if there is a driver available for your Video card.

Then install [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) the restricted formates.
Go on that page to where it says **Click here to install the ubuntu-restricted-extras package **and just do that. Follow the instruction and click on install. You'll need your password.

If you use an on board video card:
Go into your bios and see if you can share more memory to your video card.

Also go to **System / preferences / Appearance/ **here click on ** Visual effects **and check mark **none**
If firefox does not play flash videos in full-screen install **opera browser **
Or play the videos in VLC 

Open the folder** Home**  push **ctrl+H **now you can see the hidden files.
go to **Mozilla/ **Firefox /*** **.default**/ **Cache /**Every time you click on a youtube video a file will be created in this folder. After starting the video in your browser, just right click on the new file you see and open it with VLC or totem.
Hope that helped!

---

### Post by ddimit on 2011-05-27
im running ubuntu 11.4 (why do i have to install ubuntu 10.4?)
i have ati x1300 card
i already have ubuntu restricted extras 
and still nothing 
i have also installed ati hacks for vlc but still nothing 
i have used 10 video players but with no succeed 
the ati new catalyst version does not support my graphic card so maybe after some time when i will buy new pc i may come back to ubuntu if the new catalyst version (11.4) fixes all the problems

---

### Post by Joe of loath on 2011-05-27
What processor do you have, and what videos (resolution, codec, source drive) are you trying to play?

---

### Post by ddimit on 2011-05-27
intel core duo and im trying to play mkv video files from the hard disc
720p and 1080p

---

### Post by Joe of loath on 2011-05-27
Sounds like the video card drivers, then. I can play 720p videos on my PC with integrated graphics (Intel 4500hd), but not 1080p.

---

### Post by LordNeo on 2011-05-27
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by linuxinstalledfromhdd on 2011-05-27
This is a great example of why I don't recommend ATI graphics with Ubuntu. ):P

---

### Post by Joe of loath on 2011-05-27
Same here. I have an nVidia FX5200, and the 173xx drivers 'just worked' on Debian.

---

### Post by lovinglinux on 2011-05-28
I don't have an ATI card, but this is what I do to improve performance and watch HD video.

First open *gstreamer-properties*, click the *Video* tab, click the *Plugin* menu in the *Default Output* section, select **X Windows System (X11/Vshm/Xv)**.

Install smplayer:

```
sudo apt-get install smplayer
```

Open it, then open the Preferences (CTRL+P). Select *General* on the left panel, select the *Video* tab on the right panel. Make sure the Output driver is set to xv. 

Select *Performance* in the left panel, tick "Allow frame drop". In the loop filter, select "Skip only on HD videos".

---

### Post by crispy_420 on 2011-05-28
[http://www.omgubuntu.co.uk/2010/11/force-flash-gpu-acceleration-in-linux-improve-performance/](http://www.omgubuntu.co.uk/2010/11/force-flash-gpu-acceleration-in-linux-improve-performance/)

Helped me...

---

