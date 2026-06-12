---
title: "Youtube is Lacking"
date: 2009-09-15
forum: General Help
---

### Post by libak on 2009-09-15
Hello There,

I'm using Firefox and when I try to watch a youtube clip the movie is lacking.
I have a dual-boot setup on my computer and I watch youtube clips fine in windows. There is also no problem with watching movies in Ubuntu that are stored on the hard-drive of the computer.

Hope you can help.

Greets 
Lars

---

### Post by tom66 on 2009-09-15
Are you using Adobe's flash plugin or one of the open source ones?

---

### Post by libak on 2009-09-15
I'm using the Adobe flash plugin

- Lars

---

### Post by jzacsh on 2009-09-15
i notice a really annoying lag whenever i watch any flash video players in their full screen mode (no matter which type of flash installation i try). is it in full screen mostly? or just the same either way?

---

### Post by mysoogal on 2009-09-15
here is why i hate flash so much and how much i wish to get ride of this corruption !

adobe flash is evil ! 


in another note, i've come to save you from this evil :popcorn:

check my post !

[http://ubuntuforums.org/showthread.php?t=1160792](http://ubuntuforums.org/showthread.php?t=1160792)

you dont have to use flash player !!! on youtube

im so sick from flash im going to pukeee all over

---

### Post by jzacsh on 2009-09-15
mysoogal, this looks awesome, i'm going to try this asap.

---

### Post by NoaHall on 2009-09-15
Are you using 64 bit? If so, follow this -> [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

I'm afraid that the open source ones suck. Seriously.

---

### Post by libak on 2009-09-15
> **mysoogal said:**
> here is why i hate flash so much and how much i wish to get ride of this corruption !

adobe flash is evil ! 


in another note, i've come to save you from this evil :popcorn:

check my post !

[http://ubuntuforums.org/showthread.php?t=1160792](http://ubuntuforums.org/showthread.php?t=1160792)

you dont have to use flash player !!! on youtube

im so sick from flash im going to pukeee all over

I have now installed YouTotem, but when I'm trying to open a video on youtube it returns: "YouTotem: Unable to find video source".

As it comes to Adobe Flash player. How can I check that it is the player that firefox is using and not another that I have installed by a mistake?

---

### Post by PenguinLuva on 2009-09-17
> **libak said:**
> I have now installed YouTotem, but when I'm trying to open a video on youtube it returns: "YouTotem: Unable to find video source".

As it comes to Adobe Flash player. How can I check that it is the player that firefox is using and not another that I have installed by a mistake?

Ditto. I'm having the exact same problem.

---

### Post by mysoogal on 2009-09-28
you didn't install VideoLan player, thats why your getting totem trying to play the video with codec packs not installed

you also need to install all the gstreamer plugins, the codec and audio codec for totem,

you can always just install vlc and reboot your browser. it should work as it works on mine :KS

test out your vlc plugin, if you can watch video then it should be working 

[http://vlc.revolunet.com/git/example.html](http://vlc.revolunet.com/git/example.html)

you will need at least videolan version 9.9 anything above such as vlc 1.0.0 will not work on the example.html page but it will work on youtube if you used the new version. remember thu the javascript files are built for videolan versions that are below 1.0.0 like 8.6a something like that.


it should work. maybe you guys didnt refresh your page and install vlc :KS cuz it really is working for me.

Sorry i left out VLC !!!!!!!! you will need to also install sudo apt-get install mozilla-plugin-vlc i think thats how its called. 

install everything, reboot browser and go youtube should be workin now with vlc instead of totem

:D

---

