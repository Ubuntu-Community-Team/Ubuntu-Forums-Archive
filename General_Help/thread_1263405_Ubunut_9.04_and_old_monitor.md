---
title: "Ubunut 9.04 and old monitor"
date: 2009-09-10
forum: General Help
---

### Post by steve97usa on 2009-09-10
Hi
I'm trying to recicle an old PC with Ubuntu (it's an Compaq iPaq).
I was able to install ubuntu 9.04 and is working just fine, however is not capable to recognize an LCD monitor I would like to use with that system.
The monitor is an LCD  MV140 15" Megavision.
When I connect it to the system and reboot, I end up with an X server error.
I tried to run the command "sudo dpkg-reconfigure xserver-xorg" but has no effect.
I read somewhere that the latest ubuntu release take care anyway of the monitor, so I'm not sure if make sense a manual override of xorg.conf and eventually what I should put in.

Using other monitors it works just fine but of course the point is to recycle some old HW I have around.

Thanks in advance for any help, I would like to avoid to buy a new monitor.

STeve

---

### Post by DasEi on 2009-09-11
I could give you a standard section for lcd monitor,  but it'll be your own risk to put it in xorg,  as I don't know the specs of your compaq

---

### Post by DasEi on 2009-09-11
sections you can try :

[http://paste.ubuntu.com/268926](http://paste.ubuntu.com/268926)

---

### Post by steve97usa on 2009-09-11
> **DasEi said:**
> I could give you a standard section for lcd monitor,  but it'll be your own risk to put it in xorg,  as I don't know the specs of your compaq

Thanks, it would be great.  
I'm not sure what info you need, eventually I can find something.
The PC is a Compaq iPaq with a Celeron 500 Mhz. Has 512 Mbyte Ram (the maximum the system can have) and a 8Gbyte HD. About the video card is a Compaq VGA controller, I don't have specs.
The monitor is a Megavision 14" MV140 (Megavision MV140 1024 x 768 .279mm 14" Black LCD Monitor) I bought years ago.
I found some specs here : [http://www.megavisionsys.com/products2_specs.asp?model=MV140](http://www.megavisionsys.com/products2_specs.asp?model=MV140)

So basically : 
MODEL  	MV140
Panel 	Type 	14" TFT ActiveMatrix Panel
Pixel Pitch 	0.279mm(H) x 0.279mm(V)
Display Area 	285.696mm(H) x 214.272mm(V)
Display Colors 	262,144
Contrast Ratio 	250 : 1 (Typical)
Brightness 	150 cd/m©÷(Typical)
Scanning Frequency 	Horizontal 	31 ~ 61KHz
                        Vertical 	56 ~ 75Hz
Recommended Resolution 	1024 x 768 @ 60Hz
Input Signals 	VGA 	RGB Analog
Compatibility 	Win95/ 98/ 2000/XP, Unix, Linux
User Controls(OSD) 	Auto-Adjustment, Brightness, Contrast, H/V position, Clock, Phase, Color control, 5 OSD Language

Thanks again for any help !

STeve

---

### Post by steve97usa on 2009-09-11
> **DasEi said:**
> sections you can try :


It works ! Thanks !
The only problem was the login screen and the default mode.
It was coming up always at 800x600, so I inverted the Modes selection in the xorg.conf file to have first the 1024x768 and so far everything is working great !!
Many thanks ! Now I have a nice station for minor duties (the machine is not exactly "fast" :-) ) but using Xfce is not so bad !

STeve

---

### Post by DasEi on 2009-09-11
A way to really fasten this thing is : use minimal netinstaller,  choose no soft at all and then install icewm plus all addional needed soft from the repos, with that I got a celeron 433 in a lappi (which is less then Pentium 2) to watch even avi-movie from cd

---

