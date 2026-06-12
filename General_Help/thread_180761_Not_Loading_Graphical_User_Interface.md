---
title: "Not Loading Graphical User Interface"
date: 2006-05-22
forum: General Help
---

### Post by deville75 on 2006-05-22
I've installed Ubuntu on a partition in my harddrive and it won't load the graphical user interface..  I've made a swap as well and i'm pretty sure i've installed it correctly because the Live CD says the exact same thing.

When i start in Ubuntu, right after it loads everything in that "brownish" screen it says something like "X server failed to load Graphical User interface":confused:  .. Those werent the exact words but i think you get the point.

I'm running on an AMD 64 3700+ with an Nvidia 7600Gt video card.

Can someone help me fix this?

Thanks.

---

### Post by confused57 on 2006-05-22
I'm a little short on time, but it may be a problem with your video driver,
see if there is anything on this thread that may help you:

[http://www.ubuntuforums.org/showthread.php?t=180229](http://www.ubuntuforums.org/showthread.php?t=180229)

---

### Post by nanotube on 2006-05-23
check out this link:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ)
refer to section 4.2 
it will sort you out.

---

### Post by deville75 on 2006-05-24
Hey thanks for the link.

I was wondering tho, will i be able to change the driver after i choose one.. for example if i choose "vesa" now and want to change it to Nvidia

---

### Post by nanotube on 2006-05-24
yes, sure, you can change it later, same way - either use dpkg-reconfigure method, or edit the xorg.conf file. feel free to play around - just make a backup of a working xorg.conf, so that if you change something and x doesnt start, you can restore it easily. :)

---

### Post by deville75 on 2006-05-24
Hey, thanks for the help. I'm finally using Ubuntu!  The only thing is that i'm using Vesa instead for NV for Nvidia, which would've been nice.

Right now though i'm trying to get Flash Player installed so i can browse some Flash websites.  I followed the install instructions and this is the output i get in the Terminal:  




deville75@deville:~$ cd Desktop/install_flash_player_7_linux
deville75@deville:~/Desktop/install_flash_player_7_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

---

### Post by nanotube on 2006-05-24
unfortunately, you are out of luck. there is no flashplayer for 64bit ubuntu...

---

### Post by deville75 on 2006-05-25
:S  darn that sux.. wen do u think they'll be coming out with one? Also, is it possible to play video off of Gamespot for example, i'm guessing not since they use Windows Media Player

---

### Post by nanotube on 2006-05-25
[QUOTE=deville75]:S  darn that sux.. wen do u think they'll be coming out with one? Also, is it possible to play video off of Gamespot for example, i'm guessing not since they use Windows Media Player[/QUOTE]
well, that's why you should have asked before installing whether you should use the 64bit ubuntu :) whenever someone asks that, i always say "no, use 32bit, you will save yourself some headaches". so in other words... i am not sure if there are any definite plans for 64bit flash any time soon.

as no win media player - you could try installing mplayer - this can play just about any video file. of course, i've also heard that there is some problems with codec availability for 64bit ubuntu. so you may be out of luck on that one too. but try installing mplayer package, and see.

---

### Post by deville75 on 2006-05-25
k, i'll try that, but i didnt kno i could install 32 bit ubuntu on a 64 bit system... i'm a noob.. so basically i can install my "Ubuntu for PC" instead of "Ubuntu for 64 bit"  ???  In that case i guess i might as well install 32 bit.. it shouldnt take too long to re-install.

---

### Post by nanotube on 2006-05-25
[QUOTE=deville75]k, i'll try that, but i didnt kno i could install 32 bit ubuntu on a 64 bit system... i'm a noob.. so basically i can install my "Ubuntu for PC" instead of "Ubuntu for 64 bit"  ???[/QUOTE]
yes, you can just install 32bit ubuntu on your 64bit pc, with no problems.

---

### Post by Sammi on 2006-05-25
And if you're up for the re'install, I would recomend it, as the 32 bit version will give you far less troubles and headaches. Normal 32 bit Ubuntu has got very good support for most things, so please don't get discouraged by this little setback ;)

---

