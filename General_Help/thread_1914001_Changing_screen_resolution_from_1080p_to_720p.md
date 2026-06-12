---
title: "Changing screen resolution from 1080p to 720p?"
date: 2012-01-23
forum: General Help
---

### Post by Yesirom on 2012-01-23
I'd like to record some video tutorials in 720p because it's more practical, mostly because of the file size but my screen size is 1080p.

I'm using an ATI Radeon 2600 XT graphics card and I can easily change the screen resolution via Catalyst or just using the built in Monitors feature in Ubuntu.

The only problem is when I change the resolution to 1280x720 part of the screen gets clipped. Something like this [http://i.imgur.com/UET9o.png](http://i.imgur.com/UET9o.png)

Is it even possible to make it go fullscreen?

---

### Post by sudodus on 2012-01-23
Test what screen resolutions that work using ```
xrandr
``` Without parameters it will tell which resolutions that are displayed properly by your system. Maybe 1280x720 is not, so select another resolution. See the manual how to run xrandr with options
```
man xrandr
```

---

### Post by Yesirom on 2012-01-23
I tested other resolutions from the dropdown that worked and it was great but the only problem is that those put black bars on both sides. I'll try this method out, stay tuned :)

---

### Post by sudodus on 2012-01-23
> **Yesirom said:**
> I tested other resolutions from the dropdown that worked and it was great but the only problem is that those put black bars on both sides. I'll try this method out, stay tuned :)
My system can display 960x540, which is exactly 1/4 of 1920x1080, so I get not black bars. Does it work for you?

---

### Post by Yesirom on 2012-01-23
Here is the output for **xrandr**:
```
   1920x1080      60.0 +   50.0     30.0     25.0     24.0* 
   1360x768       59.8 +   50.0     24.0  
   1280x768       59.9 +   50.0     24.0  
   1152x648       60.0 +   50.0  
   1776x1000      60.0     50.0     30.0     25.0     24.0  
   1680x1050      60.0     50.0     24.0  
   1400x1050      60.0     50.0     24.0  
   1280x1024      60.0     50.0     24.0  
   1440x900       59.9     50.0     24.0  
   1280x960       60.0     50.0     24.0  
   1280x800       60.0     50.0     24.0  
   1152x864       60.0     50.0     24.0  
   **1280x720       60.0     50.0     24.0  **
   1024x768       75.0     70.1     60.0     50.0     24.0  
   800x600        72.2     75.0     70.0     60.3     56.2     50.0     24.0  
   720x576        50.0     25.0  
   720x480        60.0     50.0     30.0     24.0  
   640x480        75.0     72.8     60.0     50.0     30.0     24.0  
```
I'm not sure what to do now, what is the difference between changing the resolution with xrandr and using something like catalyst or monitors?

---

### Post by Yesirom on 2012-01-23
> **sudodus said:**
> My system can display 960x540, which is exactly 1/4 of 1920x1080, so I get not black bars. Does it work for you?

I don't have that option

---

### Post by Yesirom on 2012-01-23
I don't have black bars when recording but when I upload the video to YouTube or Vimeo it adds those black bars because it expects 1280x720 (at least I think so, why else would they add it?).

---

### Post by sudodus on 2012-01-23
> **Yesirom said:**
> I don't have that option
But 1280x720 is listed :-) Maybe you can adjust your monitor (manually with some buttons on the edge of the monitor screen), to get the screen fit the video output.

---

### Post by sudodus on 2012-01-23
I just started thinking that maybe you can record your tutorial in full 1080p and afterwards use ***ffmpeg*** to reduce to frame size to 960x540 (let us call it 540p). Would that be OK, or would you lose too much of the fine details in the video?

---

### Post by Yesirom on 2012-01-23
I think that resizing the video later would just kill it, because I would convert it then the service like YouTube or Vimeo would convert it basically chewing it like grass.

If I can't have 720p I guess I'll record full 1080p, not ideal but at least I don't sacrifice quality.

I would try to adjust the settings physically on my monitor but it's to much of a hassle, I would then need to change them back (if they even worked) to normal.

Oh and big thanks for the help :)

And if someone else is reading this and knows of a way feel free to tell, I'm not giving up yet.

---

### Post by Yesirom on 2012-01-23
I checked in Windows, works fine there. Driver issue? I can only guess :D

---

### Post by sudodus on 2012-01-24
> **Yesirom said:**
> I checked in Windows, works fine there. Driver issue? I can only guess :D
Probably: yes. An alternative might be to run a virtual machine with a window of the desired size to create the tutorial.

---

### Post by Yesirom on 2012-01-24
> **sudodus said:**
> Probably: yes. An alternative might be to run a virtual machine with a window of the desired size to create the tutorial.
Great idea but I need good 3D capabilities. I read online about something called Xephyr, I'll give it a try.

---

