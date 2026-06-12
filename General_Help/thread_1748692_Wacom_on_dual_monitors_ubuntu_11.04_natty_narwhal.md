---
title: "Wacom on dual monitors ubuntu 11.04 natty narwhal"
date: 2011-05-03
forum: General Help
---

### Post by tonqua on 2011-05-03
Hi,
First post, new user of Ubuntu and loving it.

I recently upgraded to release 11.04.
The mapping of my wacom (graphire4) has gone awry and I don't know how to fix it.
In 10.10 I edited the 50-wacom.conf file with: 
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf

and added 

Option "KeepShape" "on"as show in this link: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Upgrading to 11.04 has undone it and editing the file doesn't seem to change anything.
The 4/3 tablet is mapped over onto the dual monitor (laptop 1600x900 and external  1920x1080) so circles are drawn as ovals.

I couldn't find any help on how to remap in natty narwhal. I would very much welcome any help on how to remap  my wacom to the dual monitor setup.

Thank you.

---

### Post by Favux on 2011-05-03
Hi tonqua,

Welcome to Ubuntu forums!

KeepShape has been removed from xf86-input-wacom at least temporarily.  You can use the new xsetwacom Parameter MapToOutput or if you are using the proprietary Nvidia drivers the CTM method.  See:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

---

### Post by tonqua on 2011-05-04
Hey Favux,
Thank you for the answer.
I read the link. I must admit ... I didn't understand any of it.
I have a Graphire4 and I think an ATI graphics card. I tried following the instructions but I get blocked pretty quickely. "Cannot find device 'Wacom Graphire4'"
In 10.10 I added one line of code to the wacom configuration file, adding the MapToOutput line and it worked fine.
Is it really that much more complicated now?

---

### Post by Favux on 2011-05-04
No, it isn't any more complicated.

You should just be able to find your "device names" from *xinput list*.  Then find the monitor you want to map to in the output of *xrandr*.  What do you see with them?

---

### Post by tonqua on 2011-06-26
It worked!
Sorry it took quite a while but I moved houses and only just got connected this week.

So my problem was that my old wacom was incorrectly mapped to the dual monitor resulting in making ellipses when I drew circles.
I tried to understand the matrix method you linked to but couldn't quite get it, I went for the xsetwacom command to remap the height of the wacom area.

my dual monitor setup is, acording to *xrandr* : 3520 x 1080 pixels or a 3.26 ratio
*xinput --list* told me I had a Wacom *Graphire4 6x8 stylus*
*xinput list-props "Wacom Graphire4 6x8 stylus"* told me the *Wacom tablet area* was *0, 0, 16704, 12064* or a ratio of 1.38
So to get my tablet 1.38 ratio to match my screen 3.26 I had to multiply the height by 1.38/3.26=0.42
Instead of a tablet 16704x12064 I would have 16704 by 5066
so I tried* xsetwacom set "Wacom Graphire4 6x8 stylus" Area 0, 0, 16704, 5066*
and it worked,
my circles are round again.
to make it stick through reboot I created a .xsetwacom.sh in my /home/user/ folder in the properties/permissions of the file I checked "allow executing file as program"
and added to system>preferences>startup aplications the command *sh /home/user/.xsetwacom.sh*
that didn't work so I also put in the terminal: *chmod +x ~/.xsetwacom.sh*
not sure which one of the two works but now when i restart I can draw circles.
Thank you Favux for all the info :D.
Hope it helps ppl with a similar problem.

---

