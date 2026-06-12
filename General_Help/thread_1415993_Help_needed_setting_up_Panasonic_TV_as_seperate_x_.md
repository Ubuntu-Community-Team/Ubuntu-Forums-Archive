---
title: "Help needed setting up Panasonic TV as seperate x screen"
date: 2010-02-25
forum: General Help
---

### Post by daimaru on 2010-02-25
using ubuntu 9.10
quick summary: need to set my tv resolution to 1840x1036 to see the whole desktop without cropping

hi i just got a panasonic plasma tv and am trying to use it to watch movies from my computer. I hooked it up using my graphic card's dvi out. Since the TV came with a dvi to hdmi adapter I just had to buy a hdmi cable and now its set up to run under 1080p input. 

So I got 1920x1080 resolution for the tv. The problem is that the resolution does not fit exactly into the tv's screen. I am missing about 30 pixels top & bottom and some on the sides too. This results in me seeing my desktop on my tv, but the top panel with the applications menu etc is just out of bounds. 

Under windows xp I have the same problem, but the nvidia control panel there has an option to "Adjust desktop size and position" which kind of works. Well you can resize but you cant position the picture. Resizing makes my actual resolution 1840x1036 pixels. With that resolution my left rigth top and bottom edges are all inside the TVs screen. 

Now i tried to do this in ubuntu using nvidia-settings and manually editing xorg.conf, but I am having no success at all. Nvidia or the x server or something is totally ignoring any modlines I include for my second screen (tv), and always shows 1920x1080 ... 

I have no way to scale the picture from the tv menu so I need to scale it in ubuntu. Does anyone know how to do this ?

---

### Post by daimaru on 2010-04-02
had to install newest nvidia drivers (195.36.03) there you have the option to correct overscan ...

---

