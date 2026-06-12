---
title: "Transparent Windows?!?"
date: 2006-05-06
forum: General Help
---

### Post by clay on 2006-05-06
does anyone know how i can get transparent windows? i been trying to search on google, google/linux. and nothing. any help would be awsome!:D

---

### Post by MetalMusicAddict on 2006-05-06
Search the forums for XGL and Compiz.

---

### Post by wikiguy on 2006-05-06
is not necessary you can also download xcompmgr like this

$ sudo apitude install xcompmgr transset

then

$ sudo gedit /etc/X11/xorg.conf

add this to the end of the file

[COLOR="Red"]Section "Extensions"
	Option 	"Composite" "Enable"
EndSection[/COLOR]


THEN IN SECTION DEVICE YOU MUST PUT THE FOLLOWING THINGS

[COLOR="Red"]FOR NVIDIA CARDS

	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 

FOR ATI CARDS

        Option          "backingstore"          "true"
	Option 		"AllowGLXWithComposite" "true" 
[/COLOR]

AND THEN YOU MUST TYPE IN THE TERMINAL

$ xcompmgr -CcFF

it looks super sweet:D :D so finally you do a 

$ killall gnome-panel

then you can open a terminal a type for example

$ transset 0.75

ENTER AND THEN RIGHT CLICK IN SOME WINDOWS THIS APPLIES TO EVERYONE AND..... BANG !!! THE WINDOW IS TRANSPARENT

BY THE WAY IF YOU WANT TO GO TO SYSTEM>PREFERENCES>SESSIONS>AND AND THIS COMMAND IN ORDER TO BE STARTED EVERY TIME YOU TURN ON THE COMPUTER.:p

---

### Post by ZylGadis on 2006-05-07
Last I heard, xcompmgr was rather unstable. Anyway, it is a dead end developmentwise, so he should stick with xgl/compiz.

---

### Post by JoeMetal on 2006-05-07
Right now transset is the only way to do true transparency.  It hasn't been implemented in XGL/Compiz as of yet.

---

### Post by wikiguy on 2006-05-07
now im using this repositories if you want to add them

sudo gedit /etc/apt/sources.list

then you copy this to the end of the file

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

and....sudo apt-get update

look for compiz in synaptic and install compiz vanilla and gset compiz this last is to cofigure compiz options this compiz has everything working even wobbly(i had some problems with this in other versions)

The last thing your videos may slow down a little im not sure why mayde is my Nvidia Geforce 440 MX of 64 mb i dont know:(  but i hope you dont get these problems

---

### Post by phorque on 2006-05-10
[QUOTE=wikiguy]is not necessary you can also download xcompmgr like this

$ sudo apitude install xcompmgr transset

then

$ sudo gedit /etc/X11/xorg.conf

add this to the end of the file

[COLOR="Red"]Section "Extensions"
	Option 	"Composite" "Enable"
EndSection[/COLOR]


THEN IN SECTION DEVICE YOU MUST PUT THE FOLLOWING THINGS

[COLOR="Red"]FOR NVIDIA CARDS

	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 

FOR ATI CARDS

        Option          "backingstore"          "true"
	Option 		"AllowGLXWithComposite" "true" 
[/COLOR]

AND THEN YOU MUST TYPE IN THE TERMINAL

$ xcompmgr -CcFF

it looks super sweet:D :D so finally you do a 

$ killall gnome-panel

then you can open a terminal a type for example

$ transset 0.75

ENTER AND THEN RIGHT CLICK IN SOME WINDOWS THIS APPLIES TO EVERYONE AND..... BANG !!! THE WINDOW IS TRANSPARENT

BY THE WAY IF YOU WANT TO GO TO SYSTEM>PREFERENCES>SESSIONS>AND AND THIS COMMAND IN ORDER TO BE STARTED EVERY TIME YOU TURN ON THE COMPUTER.:p[/QUOTE]

Doesn't do jack for me. Weird.

---

