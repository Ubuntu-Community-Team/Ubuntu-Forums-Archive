---
title: "Screen resolution issues."
date: 2009-09-28
forum: General Help
---

### Post by MoonlitFate on 2009-09-28
[FONT=Palatino Linotype][SIZE=2][COLOR=Blue]So, I'm pretty confused, and don't know how to fix the problem I'm having. ._.; Basically my screen resolution in Ubuntu was limited to 1024 x 768 (the max resolution on my monitor is 1280 x 1024), so I looked up how to try and fix that.  I did find something, that involved editing my xorg.conf file, which I did and it does allow the max resolution.  But the problem is the aspect ratio it's 5:4, and I need to somehow change that to 4:3.

If anyone can help me, I'd appreciate it greatly.  And preferably something step-by-step (I'm not very Ubuntu savvy, yet. :p) [/COLOR][/SIZE][/FONT]

---

### Post by BAMF1501 on 2009-09-28
Have you installed your graphic driver s//

---

### Post by MoonlitFate on 2009-09-28
Do I really need them? Granted, I have an older graphics card... ATI FireGL 8800, and when I search for said drivers on ATI's website, I am directed to a page that has a 404 error. :(

---

### Post by CatKiller on 2009-09-28
> **MoonlitFate said:**
> But the problem is the aspect ratio it's 5:4, and I need to somehow change that to 4:3.

You want 1280×1024, but you want the ratio between those numbers to be 4×3? Let me know when you've changed the laws of mathematics, because I've got some sums that I'll probably have to do again...

If you want that ratio, and you want that width, you need 1280×960. Not all monitors will do that resolution.

---

### Post by diesch on 2009-09-28
Typing ```
xrandr
``` in a Terminal window will list all resolutions you can use.

---

### Post by MoonlitFate on 2009-09-28
> **diesch said:**
> Typing ```
xrandr
``` in a Terminal window will list all resolutions you can use.

I typed that into the terminal and got this: ```
Screen 0: minimum 320 x 200, current 1280 x 960, maximum 1280 x 1024
VGA-0 connected 1280x960+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x1024      59.9 +   60.0  
   1280x960       60.0* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)

```

---

### Post by diesch on 2009-09-28
So currently you have 1280x960 (4:3 ration) but 1280x1024 (5:4) is the default mode.

To make 1280x960 the default you can edit /etc/X11/xorg.conf and add the following to the "Screen" section:
```

DefaultDepth    24
SubSection "Display"
            Depth           24
            Modes   "1280x960" "1280x1024"
EndSubSection

```You may add some more modes to the Modes line if you want.

If that doesn't work please attach your  /etc/X11/xorg.conf

---

### Post by CatKiller on 2009-09-29
Or you can use ```
        Option          "PreferredMode"                 "1280x960"

``` in the Monitor section.

---

### Post by kjohri on 2009-09-29
Try

System -> Administration -> Hardware Drivers.

See if there is third party graphics driven that can be installed.

---

### Post by MoonlitFate on 2009-10-01
I fixed the problem, I just needed to select 1280 x 1024, and fiddle around with the actually monitor settings.  Thank you to everyone who replied to this thread, and I apologise if I wasted anyone's time. ._.

---

