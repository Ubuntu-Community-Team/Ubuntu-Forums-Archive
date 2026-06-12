---
title: "Problems adding background to GRUB OS Choice menu!"
date: 2009-12-06
forum: General Help
---

### Post by madmax.santana on 2009-12-06
I have played with legacy grub and edited the menu.lst file several times. I wanted to do something with the new GRUB2 or grub 1.97 which comes by default with the Ubuntu Karmic. 
Well I heard that you could actually set-up grub to contain a display image. 
I used this link here "https://wiki.ubuntu.com/Grub2" as a tutorial and edited the 05_debian_theme file to contain a background image for GRUB. Then I executed the command update-grub and it said that it had found the Debian Background File named GrubWall.png. I had already taken care of dithering the image to 14 colors. Well, that means everything seems fine on my end.
Now when I reboot, grub is the same. Meaning there has been no image added to the grub. Any ideas on why and how?

---

### Post by audiomick on 2009-12-06
Here is another Grub2 tutorial. Maybe there is something in there.
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by madmax.santana on 2009-12-06
@audiomick: Thanks pal, for your post but unfortunately this tutorial is almost the same as the tutorial I mentioned. It tells me how to add a splash image to my grub. I have done so exactly so many times over and over, from the start. But still, I do get the line "Found Debian background xxxx.tga" But when I reboot, it doesn't appear. Will be very thankful if anyone could identify what is the problem with what I am doing.

---

### Post by Dedoimedo on 2009-12-09
Section use_bg=false, change to use_bg=true.
Dedoimedo

---

### Post by madmax.santana on 2009-12-22
@Dedoimedo:
I didn't understand your comment. Where is this section? In which file?

Anyway, I got it going with a fresh installation of Ubuntu and Startup Manager in Ubuntu 9.10. But I still would like to know what wrong was I doing before?

---

### Post by Dedoimedo on 2009-12-23
In the debian_theme file, there's a line that says use_bg=<something>.
To see background images, this line needs to be use_bg=true. Change it from false, rebuild the grub, reboot and you'll have the images you want as the grub menu background.
Dedoimedo

---

### Post by madmax.santana on 2009-12-23
OH K!!! I got it... Thanks a lot...

---

### Post by Dedoimedo on 2009-12-23
Excellent, mark the thread as solved ... oh you did, great!
Dedoimedo

---

