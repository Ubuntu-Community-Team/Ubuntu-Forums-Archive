---
title: "[B][/B] VLC stops for 5 seconds while doing fullscreen"
date: 2010-03-31
forum: General Help
---

### Post by piyushchandrakar on 2010-03-31
there are few problems that i am facing

1. while playing any video file in VLC or any other player, i try to fullscreen or back to normal then the VLC just stopped for 5-7 seconds, video is running but in the screen it does not show running just sound comes.

2. while i open firefox or maximize it from clicking on taskbar, it take time similar thing the nautilus do when its going to maximize.

i don't know what the problem is, sometimes i feel it is because of compiz and emerald effact, but when i was ubuntu8.10 user, there was not such problem, it runs smooth.

i personally feel the response rate slower using karmic.

---

### Post by ajgreeny on 2010-03-31
Most likely a graphics card/driver problem, I think, but you don't give any clues about your hardware, so let's see what that is and there may be more clues about where to go.

---

### Post by piyushchandrakar on 2010-03-31
HP pavilion dv5 1006ax Laptop
ATI mobility Raedon 3450 graphics 256mb
ATI Drivers installed
3GB ram

---

### Post by eltonw on 2010-03-31
> **piyushchandrakar said:**
> HP pavilion dv5 1006ax Laptop
ATI mobility Raedon 3450 graphics 256mb
ATI Drivers installed
3GB ram
... just a suggestion: you did not mention your current display resolution. How about changing that to a lower resolution and then try running VLC in full screen? Also do you have other apps running in the background? (e.g. Boinc / Seti@Home, etc...)

HTH,

greeitings from Montreal (Quebec), Canada;)

---

### Post by piyushchandrakar on 2010-03-31
i have tried to change the resolution...........
but no way..

---

### Post by asn_knight on 2010-04-03
Hey!
I have the same problem. Its bcoz of the Graphics Card Driver(I too hav 3450). It seems the new ATI driver has some bug or so. Anyway I saw a blog which seems to claim tht he has slved it. but didnt work out for me. Just try and letme know if this works.
[http://blog.desair-homble.be/#post50](http://blog.desair-homble.be/#post50)
(At the end he has mentioned abt slow resize)

Enjoy,
--asn_knight--

---

### Post by asn_knight on 2010-04-03
WOHOa!!! I found a solution!!! Workin very well for me...No VLC lag now..no maximizing lag!!!! Cool!!!
Check th last but 1 post of 
[http://ubuntuforums.org/archive/index.php/t-1107559.html](http://ubuntuforums.org/archive/index.php/t-1107559.html)

Amazing!!! Now I will undoubtedly tell Ubuntu effects are better thn Windows..
Atlast after reinstallin Ubuntu 2-3 times for this bug its workin too good!!! 

Enjoy,
--asn_knight--

---

### Post by piyushchandrakar on 2010-04-04
People those Who are using the Ubuntu Karmic with ATI Mobility raedon HD3450

this is the solution..
Easy take a breath..
Just add below PPA to your to your repository


open the software sources

system>administration>software sources

click on other software tab
below just click on add

ppa:launchpad-weyland/xserver-nobackfill

(paste above PPA and just click add source)

open your Terminal than update

Sudo Apt-Get Update

just restart the system......

hope after doing this you will enjoy the system without the LAG....

{i found it here, it worked for me

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackf](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackf)

read the READC comment the 3rd last
http://ubuntuforums.org/archive/index.php/t-1107559.html}

Thanks for reading

---

### Post by piyushchandrakar on 2010-08-22
For Lucid User (Ati mobility raedon 3450)

Open terminal and type    

 sudo add-apt-repository ppa:info-g-com/xserver-xorg-1.7.6-gc


then type:

    sudo apt-get update


wait until it finish

then type:

    sudo apt-get upgrade

---

### Post by piyushchandrakar on 2010-11-24
[https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc](https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc)

[http://www.uluga.ubuntuforums.org/showthread.php?p=9200920](http://www.uluga.ubuntuforums.org/showthread.php?p=9200920)

:p

---

