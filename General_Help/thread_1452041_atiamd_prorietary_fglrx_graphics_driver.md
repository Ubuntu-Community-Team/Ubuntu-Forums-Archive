---
title: "ati/amd prorietary fglrx graphics driver"
date: 2010-04-11
forum: General Help
---

### Post by benjaminad on 2010-04-11
:confused:   I have a Toshiba Satellite L505D-s5965 that I run super os 9.10 on. My main use for this machine is running blender. I use both blender 2.49b and blender 2.5. The problem I am having is if I do not install the graphics driver listed in my title, 2.5 will not run properly. It is super slow. Blender 2.49b runs good enough without it. When I do install that graphics driver Blender 2.5 runs GREAT but 2.49b gets completely wacked out when I try to run it. The screen goes in and out with static and if you do get it to run none of the shortcuts work and half of the blender buttons don't work either. Is there a graphics driver out there that will improve both programs? It will be a bummer if I have to install and uninstall this driver when switching between blender 2.49 and blender 2.5.

---

### Post by Cracauer on 2010-04-11
> **benjaminad said:**
> :confused:   I have a Toshiba Satellite L505D-s5965 that I run super os 9.10 on. My main use for this machine is running blender. I use both blender 2.49b and blender 2.5. The problem I am having is if I do not install the graphics driver listed in my title, 2.5 will not run properly. It is super slow. Blender 2.49b runs good enough without it. When I do install that graphics driver Blender 2.5 runs GREAT but 2.49b gets completely wacked out when I try to run it. The screen goes in and out with static and if you do get it to run none of the shortcuts work and half of the blender buttons don't work either. Is there a graphics driver out there that will improve both programs? It will be a bummer if I have to install and uninstall this driver when switching between blender 2.49 and blender 2.5.

Which driver, specifically, do you have in use when you don't use the closed-source driver? Please post your Xorg.0.log.

In general this is a little expected as the OpenSource driver is incomplete and just doesn't support all extensions that Blender might use, or it might even have a lame implementation of an extension that then doesn't work well. There might be a way to turn such extensions off in the X11 server, or in Blender. You would have to ask the Blender people about this.

You won't have to switch between drivers, strictly speaking. You can run two X11 servers. Although that normally works fine (I do that all the time for things like "this X11 server is for when I use a projector") the problem is that the closed-source driver probably doesn't really coexist with the OpenSource one. In that case you would have to do some file shuffling before that works.

Trying a newer OpenSource driver won't hurt, of course. First thing to try.

---

