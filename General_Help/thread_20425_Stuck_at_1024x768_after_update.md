---
title: "Stuck at 1024x768 after update"
date: 2005-03-16
forum: General Help
---

### Post by baza41 on 2005-03-16
After todays update on my Hoary box my screen is stuck at 1024X768 for it's max resolution, before I was running 1280X1024. I ran xorgconfig, but no joy.

---

### Post by daniels on 2005-03-16
Could you please attach /var/log/Xorg.0.log as well?

---

### Post by baza41 on 2005-03-17
OK, here's the file

---

### Post by i3dmaster on 2005-03-18
[QUOTE=baza41]OK, here's the file[/QUOTE]


I am having the same problem. I was able to get 1600x1200 but now, one level down.

---

### Post by bored2k on 2005-03-18
[QUOTE=i3dmaster]I am having the same problem. I was able to get 1600x1200 but now, one level down.[/QUOTE]
 Did you reconfigure xorg ?

---

### Post by c_dog on 2005-03-18
[QUOTE=baza41]After todays update on my Hoary box my screen is stuck at 1024X768 for it's max resolution, before I was running 1280X1024. I ran xorgconfig, but no joy.[/QUOTE]

Your driver line in your xorg.conf is "vga" which has a max res of 1024x768. You need to be loading a card specific driver for higher non "standard VGA" resolutions.

---

### Post by i3dmaster on 2005-03-18
[QUOTE=bored2k]Did you reconfigure xorg ?[/QUOTE]

yes, I did dpkg-reconfigure xserver-xorg, and actually it seems like detecting my 2001FP monitor correct and has the 1600x1200 resolution checked. But I can only get virtual size of that and the actual resolution is still 1280x1024. How to fix this weird thing?

---

### Post by i3dmaster on 2005-03-18
[QUOTE=i3dmaster]yes, I did dpkg-reconfigure xserver-xorg, and actually it seems like detecting my 2001FP monitor correct and has the 1600x1200 resolution checked. But I can only get virtual size of that and the actual resolution is still 1280x1024. How to fix this weird thing?[/QUOTE]


Here is the xorg.conf file

---

### Post by i3dmaster on 2005-03-18
Problem solved. The tricky is DO NOT load DDC module.

You can either comment out 
Load    "ddc"

Or under the "Device" section, add this line:
Option                  "NoDDC"                      "true"

---

### Post by Leif on 2005-03-23
I've got the same problem here, old s3 worked at 1280x1024 with xfree, down to 1280x768 with xorg. I've tried to reconfigure, nothing really changes. Can anybody give me a pointer ? When I try 1280x1024 all I get is a black screen, and a noise I'm sure meaning my monitor is in pain. Do I need to play around with monitor settings (depite the fact that they were set higher in xfree and worked fine) ?

I've attached xorg.conf, the commented lines in the s3 display were the settings made by reconfigure.

I've also tried commenting out dri, ddc. No luck.

---

