---
title: "Video Editor Program?"
date: 2006-04-06
forum: General Help
---

### Post by Goober on 2006-04-06
Hello,

I am looking for a Video Editing Program for Linux.  I have tried to search around, but, well, im not quite sure what im looking for or what im doing.  I have some large video files that I need to split so I can burn them to CD (700Mb).  I am trying to copy everything on my computer harddrives to CD.  This is mostly because I simply don't trust my old computer anymore.  My gut indicates that it will crash soon, and I want to save as much as possible before that happens, if it does.

So what I am looking for is a relatively simple, easy-to-use program to split .avi movie files into smaller ones I can burn onto CD.  If anybody could point me out to such a program, I would be very grateful.

Thanks in advance,

Goober.

---

### Post by renzokuken on 2006-04-06
i think kino is a pretty simple video editor

failing that cinelerra, but that is kind of high end, adobe premier league

---

### Post by kingmonkey on 2006-04-06
If all you want to do is split files then you can use the command split:

 split --bytes=700m your.avi outputfilenames

---

### Post by edwina on 2006-04-06
There seem to be a few file splitting programs around. Probably much easier than getting into video editing software.

Try gfsplicer (it's in Synaptic) maybe. Google "split archive ubuntu" and plenty of options pop up.

Good luck, and let us know how you get on.

---

### Post by Goober on 2006-04-06
Well, thanks a lot for the quick replies!

Kino is only for a certain type of files from Camcorders, not what I have, apparently.  I was unable to find gfsplicer.  I tried the Command Line version, which I would prefer to use, but, well, I kinda forgot how to change folders.  Once I figure out how to do that (I recall a thread on that around here somewhere), then I can try that.

Synpatic just failed to find cinelerra, but I'll keep on looking for that.  

Thanks again for the help, muchly appreciated!

---

### Post by renzokuken on 2006-04-06
cinelerra is a bit overkill for what u need but incredibly cool to have anyway, its amazing

to get it u need to go to the official website (google for it) and download the rpm version, convert the rpm to a deb using alien, then install the deb

---

### Post by Goober on 2006-04-06
Actually, I found a .deb version of Cinelerra from here:

[http://www.ftconsult.com/twiki/bin/view/Cinelerra/Debian](http://www.ftconsult.com/twiki/bin/view/Cinelerra/Debian)

I got the most recent version of it, 2.0, and now I am attempting to remember how to unzip and install those kinda files.  I remember it was apt-get install or something, but ohh boy, its been a couple months since I last used Linux and it shows, lol.  I think I've got it though.  Maybe.

---

### Post by renzokuken on 2006-04-06
if u got a deb then just do 

# sudo dpkg -i cinelerra-2.0.deb

or whatever the name of the deb is

---

### Post by wh0rd on 2006-04-12
[QUOTE=renzokuken]if u got a deb then just do 

# sudo dpkg -i cinelerra-2.0.deb

or whatever the name of the deb is[/QUOTE]

Can someone put up a link for the deb package?

---

### Post by adamkane on 2006-04-24
How to install Cinelerra on Ubuntu:
[http://cvs.cinelerra.org/getting_cinelerra.html](http://cvs.cinelerra.org/getting_cinelerra.html)

---

### Post by Jens Willem on 2006-04-24
If you just want an easy-to-use program to split videos, i think Avidemux is a good choice: [http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)

It's not a complete NLE like Cinelerra, but it's extremely useful for things like that.

---

