---
title: "Dell DJ 2nd Gen not recognized"
date: 2011-01-23
forum: General Help
---

### Post by ghost25 on 2011-01-23
Got a question for whoever can answer (and I apologize if this is the wrong section, couldn't find anything that seemed to match where I needed to post this).

I've just picked up a Dell DJ 2nd Gen MP3 player from a friend and, while it would work with Windows (I tested it on my room-mate's girlfriend's laptop before I bought it) absolutely nothing happens with Ubuntu 10.04.

If I open terminal and type "lsusb" I can see it, and it's properly recognized. However, I don't know offhand where it would be mounted, as I'm not good yet with recognizing the physical addresses presented in CLI.

I have Rhythmbox, Banshee, and Amarok installed, and none of them will recognize it. I can't locate it anywhere in Computer, and it doesn't show up as would a typical flash drive. At the moment it charges with no problem, but will not sync with my machine.

I've heard that Gnomad 2 will work, but I can't seem to find it. It's installed, I know because I just installed it from Ubuntu Software Center, but I can't locate it anywhere and I don't know how to run it from CLI.

If I absolutely have to, I can run it from my Windows 7 box connected to my multimedia network, but I would really prefer to eliminate the Windows from the equation if at all possible.

Thanks in advance for the help, and let me know if you need any more information, I'll do my best to get the relevant info you need.

EDIT: Okay, I got it figured out. A multimedia device like this apparently draws too much of a load for it to work on an extension cable, especially if said cable is already attached to a USB hub. I managed to get gnomad2 to work also, by reinstalling it. [http://gnomad2.sourceforge.net/?](http://gnomad2.sourceforge.net/?) if you want to check it out.

---

