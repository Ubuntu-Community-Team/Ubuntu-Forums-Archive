---
title: "Monitor is detected as laptop"
date: 2012-09-30
forum: General Help
---

### Post by snipeshot on 2012-09-30
I recently installed Ubuntu. My monitor is detected as a laptop and I can't change my resolution higher than 1024x768. My monitor is 1440x900.

---

### Post by daslinkard on 2012-09-30
> **snipeshot said:**
> I recently installed Ubuntu. My monitor is detected as a laptop and I can't change my resolution higher than 1024x768. My monitor is 1440x900.
Could it be as simple as a driver issue? Have  you looked for restricted drivers that might be available for the  graphic card you're using? (You can do this from the "restricted  drivers" option in the menus)

---

### Post by idoitprone on 2012-09-30
```
xrandr -q 
```?

---

### Post by snipeshot on 2012-10-02
> **daslinkard said:**
> Could it be as simple as a driver issue? Have  you looked for restricted drivers that might be available for the  graphic card you're using? (You can do this from the "restricted  drivers" option in the menus)

I can't find a  "restricted  drivers" option.

---

### Post by snipeshot on 2012-10-02
> **idoitprone said:**
> ```
xrandr -q 
```?
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0

---

### Post by daslinkard on 2012-10-02
What happens when you run the following sudo command?
```
sudo jockey-gtk
```

---

### Post by snipeshot on 2012-10-02
> **daslinkard said:**
> What happens when you run the following sudo command?
```
sudo jockey-gtk
```
It says
(jockey-gtk:2023): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2023): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

then opens a program called additional drivers, which says no proprietary drivers are in use on this system.

---

### Post by dino99 on 2012-10-02
google around "ubuntu yourmonitormodel"

often such kind of issue is due to how the monitor is linked (vga/hdmi/...) or the cord itself.

and which is the graphic card/chipset used ?

---

### Post by surfer on 2012-10-02
is your monitor connected directly to the computer or is there a kvm switch in between? ...believe it or not, but this can make a difference (and can be cured).

---

### Post by snipeshot on 2012-10-02
> **surfer said:**
> is your monitor connected directly to the computer or is there a kvm switch in between? ...believe it or not, but this can make a difference (and can be cured).
 It is connected directly

---

### Post by snipeshot on 2012-10-02
> **dino99 said:**
> google around "ubuntu yourmonitormodel"

often such kind of issue is due to how the monitor is linked (vga/hdmi/...) or the cord itself.

and which is the graphic card/chipset used ?

[http://ubuntuforums.org/showthread.php?t=1265282](http://ubuntuforums.org/showthread.php?t=1265282)
this forum uses the same monitor model, but a different chipset.

My monitor is linked by vga, the problem cant be the cord because the resolution works on windows.

My computer has an intel chipset.

maybe this driver will fix the problem
[http://intellinuxgraphics.org/2012.07.html](http://intellinuxgraphics.org/2012.07.html)
but i can't install it, typing ./configure into terminal gives a long page of code and says at the end

 "configure: error: Package requirements (libdrm_intel >= 2.4.29) were not met:

No package 'libdrm_intel' found"

typing make and make install gives " make: *** No targets specified and no makefile found.  Stop."

---

### Post by snipeshot on 2012-10-03
bump

---

### Post by snipeshot on 2012-10-13
I fixed the problem by installing ubuntu 64 bit on my 32 bit system

---

