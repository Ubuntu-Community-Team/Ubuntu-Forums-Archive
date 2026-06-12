---
title: "No video mode large enough for 1280x1024 Segmentation fault"
date: 2009-09-24
forum: General Help
---

### Post by Wilbefast on 2009-09-24
Hi again folks,

I'm trying to get a game called "Lugaru" working on Ubuntu - it's cross platform and works fine on linux for everyone I've asked. When I run it from the terminal however I simply get:

[B]SDL_SetVideoMode() failed: No video mode large enough for 1280x1024
Segmentation fault[/B]

I've asked for help on [their forum]("http://forums.wolfire.com/viewtopic.php?f=7&t=5495&p=90551#p90551") and it seems like I should be adding a metamode for the Nvidia display setup or something - I won't repeat here what was said on the other thread. The reason I've come here is that I can't follow their directions suggested because I get another error when I try to save a new metamode:

[B]Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

[/B]These are my specs:

[B]Ubuntu 9.04 (Jaunty)
Kernel Linux 2.6.28-15-generic
GNOME 2.26.1
Nivdia 8400M GS with driver version 180.44
[/B]

Please help :-k


William

---

### Post by atomizer on 2009-09-24
You have to be root to write in /etc/X11 directory.
(or use sudo or gksudo)

---

### Post by Wilbefast on 2009-09-24
That guy told me to run it as su and I was all "you don't need to be the super-user to fiddle with the Nvidia settings" - ooops #-o

Right, so I figure generally nothing ever works when you're using the GUI, because I've still got a problem even though it works if I run it as root (sudo bash, etc) 
[INDENT]**Section "Screen"**
**    Identifier     "Screen0"**
**    Device         "Device0"**
**    Monitor        "Monitor0"**
**    DefaultDepth    24**
**    Option         "TwinView" "0"**
**    _Option         "metamodes" "nvidia-auto-select +0+0"_**
**    SubSection     "Display"**
**        Depth       24**
**    EndSubSection**
**EndSection**

[/INDENT]How exactly would I "phrase" the adding of a new meta-mode? Would it be in the same doohicky (with the **"**s around it) as "nvidia-auto-select" or would it be a separate one?

I need to add  **"1024x768 +0+0**"

Thanks for all the help so far,


William

---

### Post by Wilbefast on 2009-09-26
I've looked for similar errors online - a lot of games have this problem but mostly it can be fixed but editing the game's configuration file. By default though Lugaru is set to a resolution of 1024x768 which is less than the resolution (1280x800) that the error message is talking about.

I tried setting the resolution right down to 640x480 but nothing changes, not even the error message. I can only think that my computer is trying to run the game at my "native" resolution (1280x800), even when I manually set my screen resolution down to 1024x768. Metamodes don't seem to change anything - how can I get Ubuntu to run an application with a given resolution? Please help :(


William

---

### Post by Wilbefast on 2009-09-29
Alright, I've figured out what I need to do just not how to do it: I have to edit my xorg.conf file and add in a new mode. Trouble is there's no "modes" line in the file so I'm not sure where to put it - I tried to copy an example I found but ended up with a bunch of pretty red bars all over my screen, and had to log in in text mode to revert to the backup. 

Feel I'm getting close here, any ideas?

Here's the file [xorg.txt](http://www.mediafire.com/?sharekey=53fabb3528868028b64026cfc0611236e04e75f6e8ebb871)


Thanks,

William

---

