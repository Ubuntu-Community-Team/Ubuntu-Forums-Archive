---
title: "Computer not booting to GUI, get blank screen with curser."
date: 2011-07-05
forum: General Help
---

### Post by GratefulDean on 2011-07-05
Hello again,  several months ago I installed Maverick and it worked well, but eventually I lost the GUI. I fiddled with it to no avail.  So I decided to do the Natty upgrade and it ended up not fixing the problem though I am able to boot to graphics safe mode.

I popped on this forum and a couple others but got little response and ran out of fiddle time.  SO now I have a little time to mess with this, and I REALLY want to move back over to Ubuntu so if any one is familiar with that could be the issue and what can be done to fix it I would appreciate the help.

I will check in as often as I can.  I am motivated to clear this up.

Thanks,
Dean

---

### Post by hawthornso23 on 2011-07-05
Sounds like a graphics driver problem. Information on your graphics and which driver you were using would help.

---

### Post by wildmanne39 on 2011-07-06
> **GratefulDean said:**
> Hello again,  several months ago I installed Maverick and it worked well, but eventually I lost the GUI. I fiddled with it to no avail.  So I decided to do the Natty upgrade and it ended up not fixing the problem though I am able to boot to graphics safe mode.

I popped on this forum and a couple others but got little response and ran out of fiddle time.  SO now I have a little time to mess with this, and I REALLY want to move back over to Ubuntu so if any one is familiar with that could be the issue and what can be done to fix it I would appreciate the help.

I will check in as often as I can.  I am motivated to clear this up.

Thanks,
DeanHi, run this command in a terminal
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by GratefulDean on 2011-07-06
> **hawthornso23 said:**
> Sounds like a graphics driver problem. Information on your graphics and which driver you were using would help.

Thanks,

It's Nvidia GForce 8900m

Some more info?

[IMG]http://i678.photobucket.com/albums/vv147/GratefulDeanADV/Maverick%20Meerkat/NvidiaInfo.png[/IMG]

Thanks for the help!

---

### Post by GratefulDean on 2011-07-06
> **wildmanne39 said:**
> Hi, run this command in a terminal
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

Thanks, I'll try that out later today when I have some time. 

What exactly does that do?

Thanks!
D

---

### Post by GratefulDean on 2011-07-06
> **wildmanne39 said:**
> Hi, run this command in a terminal
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

mmmkay, I did it.  A little Google Fu helped me with what the command does.  Anyway, it confirmed my above post.  Here is what Linux had to say:

01:00.0 [COLOR="Red"]VGA[/COLOR] compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev al)

I hope this can lead us in the right direction.

Thanks,
D

---

### Post by wildmanne39 on 2011-07-06
> **GratefulDean said:**
> mmmkay, I did it.  A little Google Fu helped me with what the command does.  Anyway, it confirmed my above post.  Here is what Linux had to say:

01:00.0 [COLOR="Red"]VGA[/COLOR] compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev al)

I hope this can lead us in the right direction.

Thanks,
DHi, ok that is what I was looking for, here is a link that should get you into ubuntu then you can install your graphics driver and that should get you fixed up.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by GratefulDean on 2011-07-06
> **wildmanne39 said:**
> Hi, ok that is what I was looking for, here is a link that should get you into ubuntu then you can install your graphics driver and that should get you fixed up.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

That didn't work.  :(  So I went into the nVidia x server settings and it tells me:

*You do not appear to be using the Nvidia x driver.  Please edit your sconfiguration file (just run 'nvidia-xconfig' as root), and restart the driver.*

I remember messing with this in April with no luck.  I can't find any info on how to run this from root.  

I also un-installed my 185 driver as well as the "additional Jockey-KDE" drivers from the software center then installed version 173 from the terminal.  No change.

I'm still at a loss.

:(:(:(

---

### Post by wildmanne39 on 2011-07-06
> **GratefulDean said:**
> That didn't work.  :(  So I went into the nVidia x server settings and it tells me:

*You do not appear to be using the Nvidia x driver.  Please edit your sconfiguration file (just run 'nvidia-xconfig' as root), and restart the driver.*

I remember messing with this in April with no luck.  I can't find any info on how to run this from root.  

I also un-installed my 185 driver as well as the "additional Jockey-KDE" drivers from the software center then installed version 173 from the terminal.  No change.

I'm still at a loss.

:(:(:(Hi, I am not sure it sounds like you may still be using two drivers when you uninstall make sure you right click on the package you need to uninstall and select remove completely.

---

### Post by GratefulDean on 2011-07-07
> **wildmanne39 said:**
> Hi, I am not sure it sounds like you may still be using two drivers when you uninstall make sure you right click on the package you need to uninstall and select remove completely.

Good morning,

I tried to right click in the Software Center and nothing happened.  

Frustrating.

I'm at an utter loss.  The good news is this is the most feed back I have gotten yet regarding this problem.

Thanks for your advice.

D

---

### Post by wildmanne39 on 2011-07-07
> **GratefulDean said:**
> Good morning,

I tried to right click in the Software Center and nothing happened.  

Frustrating.

I'm at an utter loss.  The good news is this is the most feed back I have gotten yet regarding this problem.

Thanks for your advice.

DHi, that is probably because you have already uninstalled the drivers, but without uninstalling with the right click remove completely it will leave configuration files behind, you can reinstall the drivers and then right click on them and select remove completely, or if you know the complete name of the driver you can run this command in a terminal.
```
sudo apt-get --purge remove packagename
```

---

### Post by niharthekadi on 2011-09-23
Unfortunately due to  humidity and carelessness i lost my main board last days.
I have now whole new CPU box and this time i have intel board and chip-set.
It has OpenGL support and good amount of on board memory.
I AM REALLY EXCITED TO SEE THE CUBE FIRST TIME ON MY OWN PC. :)

But when i put my old Hard disk in to it, GUI was lost. (it is dual boot and windowz works)
Can any one help me to get it back?
Note : i have hand over my Ubuntu installation disk to some one and i even dont have an ISO for this version of Ubuntu.

---

