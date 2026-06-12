---
title: "No minimize and maximize buttons after NVIDIA driver install"
date: 2011-10-09
forum: General Help
---

### Post by Aragant on 2011-10-09
I just install Ubuntu 11.04 and my Nividia graphic card driver 
this is what is see now............
installed CompizConfig Setting Manager and Compiz Fusion Icon amd tried everything but of no use.....

---

### Post by kensum on 2011-10-09
[Aragant]("http://ubuntuforums.org/member.php?u=1159797"); Are you using the current nvidia driver? You do not need the compiz icon, just ccsm. the picture you posted shows the title bar menu on the window and not the unity panel task manager. First open ccsm and check to make sure the unity plugin is checked. Next check in appearance the theme and window controls to see if that will put it back to default. Post back with more info on what you are using, eg, hardware and whether you are using classic or unity. The fix will be different for each.

---

### Post by Aragant on 2011-10-09
- I am using Nvidia Geforce2 Mx/Mx400 and driver version is NVIDIA-Linux-x86-96.43.20-pkg1.run

- And i log in classic mode as my hardware doesn't support unity 3D but 2D :(

and thanks for the reply will highly appreciate if somebody can tell me its solution...  ;)

waiting :popcorn:

---

### Post by Aragant on 2011-10-10
Still waiting for some help...............
Please____ Anybody_____ :(

---

### Post by Aragant on 2011-10-10
As usual Nobody Helped even mods out there i poted many threads before but never get replied...  :(
i installed ubuntu more than 8 times on my pc only because of NVIDIA DRIVER problem but i just done my 50% work by making it enable to at-least login normal mode. Following the below steps ;)

$ wget [http://www.webalice.it/bernardi82/software/fixplymouth-natty](http://www.webalice.it/bernardi82/software/fixplymouth-natty)
$ chmod +x fixplymouth-natty
$ ./fixplymouth-natty

selected video resolution 1024×768-24

now the only problem left is in ubuntu classic session i can't see window borders i did ccsm window border check option. But that didn't helped.

Praying that somebody will help me................. :)
Otherwise bye ubuntu for other long time (As, i just returned after one due to NVIDIA new driver support)

---

### Post by Slim Odds on 2011-10-10
> **Aragant said:**
> As usual Nobody Helped even mods out there i poted many threads before but never get replied...  :(
i installed ubuntu more than 8 times on my pc only because of NVIDIA DRIVER problem but i just done my 50% work by making it enable to at-least login normal mode. Following the below steps ;)

$ wget [http://www.webalice.it/bernardi82/software/fixplymouth-natty](http://www.webalice.it/bernardi82/software/fixplymouth-natty)
$ chmod +x fixplymouth-natty
$ ./fixplymouth-natty

selected video resolution 1024×768-24

now the only problem left is in ubuntu classic session i can't see window borders i did ccsm window border check option. But that didn't helped.

Praying that somebody will help me................. :)
Otherwise bye ubuntu for other long time (As, i just returned after one due to NVIDIA new driver support)

To you and other whiners,

I might remind you that:
A) This forum is FREE help from VOLUNTEERS that do this in our SPARE TIME.
B) Sometimes, no one knows the answer or WE have to research it FOR YOU.

It sounds like to me that you need to restart the windows manager. I sometimes see my window controls disappear and the solution is to restart the windows manager. I do this using the Fusion-Icon application.
```
sudo apt-get install fusion-icon
```

---

### Post by 1egoman on 2011-10-10
Acctuly, This happened to me once. Try This - Open CCSM and make sure the Window Decoration Plugin is enabled.

---

### Post by Aragant on 2011-10-10
Well thanks for Nothing [COLOR=#800000]

[/COLOR]Section "Device"
Identifier     "Videocard0"
Driver         "nvidia"
VendorName     "NVIDIA Corporation"
BoardName      "GeForce 6150"
[COLOR=#800000] Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"[/COLOR]
EndSection

Just editing xorg file did worked for

PROBLEMO SOLVEDO  :guitar:

---

