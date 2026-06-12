---
title: "MPlayer 1.0pre8 released"
date: 2006-06-12
forum: General Help
---

### Post by sYs^ on 2006-06-12
[B]MPlayer 1.0pre8: *"NeuTeam strikes back"*
[/B]
One year after the last release and a new MPlayer is out. :p

>  There have also been many enhancements to the H.264 decoder to make it a lot faster and more error-resilient. More audio and video codecs are supported. Audio/Video synchronisation has been further improved, especially on Real streams and Vorbis. 

   And that's not it yet! We have some more tricks for you up our sleeves for upcoming versions of MPlayer: experimental [DVDnav]("http://dcxx.fw.hu/") (DVD menus) support and an experimental graphical user interface for our Windows port. Please join in the testing effort so that these features don't remain experimental ;-). 
 
Further informations: [http://www.mplayerhq.hu/design7/news.html]("http://www.mplayerhq.hu/design7/news.html")

Download: 
[LIST]
[*]Switzerland 		[HTTP]("http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre8.tar.bz2") 		[FTP]("ftp://ftp1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Switzerland 2 		[HTTP]("http://www4.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Germany 		[FTP]("ftp://ftp.fu-berlin.de/unix/X11/multimedia/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Germany 2 		[HTTP]("http://studwww.ira.uni-karlsruhe.de/%7Es_doeffi/MPlayer/MPlayer-1.0pre8.tar.bz2")
[*]Sweden 		[HTTP]("http://equinox.campus.ltu.se/MPlayer/releases/MPlayer-1.0pre8.tar.bz2") 		[FTP]("ftp://equinox.campus.ltu.se/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Sweden 2 		[HTTP]("http://tranquillity.campus.ltu.se/%7Ertogni/MPlayer-1.0pre8.tar.bz2")[/LIST] 
I hope it'll be in the repos soon!

---

### Post by Boris2 on 2006-06-21
Did anyone got a package already?

I found one on ubuntu-debs.de, which seems to work quite well.
[http://ubuntu-debs.de/app/mplayer/](http://ubuntu-debs.de/app/mplayer/)

---

### Post by maka on 2006-06-21
[QUOTE=sYs^][B]MPlayer 1.0pre8: *"NeuTeam strikes back"*
[/B]
One year after the last release and a new MPlayer is out. :p

 
Further informations: [http://www.mplayerhq.hu/design7/news.html]("http://www.mplayerhq.hu/design7/news.html")

Download: 
[LIST]
[*]Switzerland 		[HTTP]("http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre8.tar.bz2") 		[FTP]("ftp://ftp1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Switzerland 2 		[HTTP]("http://www4.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Germany 		[FTP]("ftp://ftp.fu-berlin.de/unix/X11/multimedia/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Germany 2 		[HTTP]("http://studwww.ira.uni-karlsruhe.de/%7Es_doeffi/MPlayer/MPlayer-1.0pre8.tar.bz2")
[*]Sweden 		[HTTP]("http://equinox.campus.ltu.se/MPlayer/releases/MPlayer-1.0pre8.tar.bz2") 		[FTP]("ftp://equinox.campus.ltu.se/MPlayer/releases/MPlayer-1.0pre8.tar.bz2")
[*]Sweden 2 		[HTTP]("http://tranquillity.campus.ltu.se/%7Ertogni/MPlayer-1.0pre8.tar.bz2")[/LIST] 
I hope it'll be in the repos soon![/QUOTE]

how do i go about upgrading from the older version to this new one? since it's not in the repos :confused:

---

### Post by nix4me on 2006-06-21
I compiled from source and it seems to be working well.

nix4me

---

### Post by maka on 2006-06-21
[QUOTE=nix4me]I compiled from source and it seems to be working well.

nix4me[/QUOTE]

do i need to delete my previous one first?

---

### Post by hoodwink on 2006-06-27
[QUOTE=maka]do i need to delete my previous one first?[/QUOTE]
Good question. I downloaded the ....deb from the .de site. how does one go about installing this since there is a current (but vulnerable) ubuntu version installed? Is it ok to just dpkg -i ...? What will happen when a ubuntu version becomes available?

---

### Post by Anduu on 2006-06-27
Jimminy Cricket!

Speaking of updates...just now I was trying to figure out how to force this sucker to install for me and zoiks!..."updates are available' pops up and by Jesus guess what?!?

It was an mplayer update!!!

Talk aboot coincindence :p

---

### Post by FredB on 2006-06-28
I will wait for a backport. After all, 1.0pre7 is not that unusable ;)

---

### Post by mlind on 2006-06-28
Thanks for the heads up!

---

### Post by amoore on 2006-06-28
The .deb for me is complied without GUI. yes, I did use "gmplayer".

---

### Post by Arktis on 2006-07-02
1.0pre8 is still not showing up in the repos.  :(

For everyone wanting to compile on their own, do 

./configure --enable-gui and make sure you have all the correct support enabled for gui and other stuff you want/need.  If not, install the proper develompment packages, and run the command again until you're satisfied.  Make sure to install the fakeroot package too.

Then do

DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary

And you'll wind up with a nice debian package when it's done.

---

### Post by mlind on 2006-07-03
[QUOTE=Arktis]1.0pre8 is still not showing up in the repos.  :(

For everyone wanting to compile on their own, do 

./configure --enable-gui and make sure you have all the correct support enabled for gui and other stuff you want/need.  If not, install the proper develompment packages, and run the command again until you're satisfied.  Make sure to install the fakeroot package too.

Then do

DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary

And you'll wind up with a nice debian package when it's done.[/QUOTE]

I made a post about [compiling mplayer]("http://www.ubuntuforums.org/showthread.php?t=206382") on a cleanroom environment.
It's the 3rd post .

---

### Post by ashrack on 2006-07-08
I have a DEB compiled with GUI! Anybody intersted??

---

### Post by MetalMusicAddict on 2006-07-09
> **ashrack said:**
> I have a DEB compiled with GUI! Anybody intersted??

Hell yea. Id love to try it out. Mplayer used to be my fav but its been so long since a update I moved on.

Id like to test it out.

---

### Post by ashrack on 2006-07-09
Here U are:
[http://www2.arnes.si/~aurank1/mplayer-1.0pre8_1.0pre8-1_i386.deb](http://www2.arnes.si/~aurank1/mplayer-1.0pre8_1.0pre8-1_i386.deb)

ps. If U get an error about sound just change it to ESD in MPLAYER preferences

---

### Post by MetalMusicAddict on 2006-07-09
Thanx sir. Just a FYI for anyone who uses the deb. If you want a GUI install mplayer-skins from Synaptic.

How exactly is MPlayer supposed to handle aspect ratio? Pre7 from the repos made a 4:3 video stretch in fullscreen on a widescreen monitor. Pre8 does the same thing but also displays wrong in a window.

---

### Post by mintcoffee on 2006-07-09
> **MetalMusicAddict said:**
> Thanx sir. Just a FYI for anyone who uses the deb. If you want a GUI install mplayer-skins from Synaptic.

How exactly is MPlayer supposed to handle aspect ratio? Pre7 from the repos made a 4:3 video stretch in fullscreen on a widescreen monitor. Pre8 does the same thing but also displays wrong in a window.

From my experience, there's an option called 'monitoraspect' in mplayer.conf that needs to be set to 16:9 (or 16:10) for a video to stretch properly on a widescreen display.

---

### Post by ashrack on 2006-07-10
> **MetalMusicAddict said:**
> Thanx sir. Just a FYI for anyone who uses the deb. If you want a GUI install mplayer-skins from Synaptic.
Are U sure it is working like that?
Since the default folder with MPLAYER for SKINS changed from /usr/share/mplayer/[COLOR="Red"]Skin[/COLOR] to /usr/share/mplayer/[COLOR="Red"]skins/[/COLOR]

---

### Post by MetalMusicAddict on 2006-07-10
> **mintcoffee said:**
> From my experience, there's an option called 'monitoraspect' in mplayer.conf that needs to be set to 16:9 (or 16:10) for a video to stretch properly on a widescreen display.
Whats the path to mplayer.conf? I see a .mplayer folder in my home folder but no such file in it. It is a Dell 16:10 monitor. 2405.
> **ashrack said:**
> Are U sure it is working like that?
Since the default folder with MPLAYER for SKINS changed from /usr/share/mplayer/[COLOR="Red"]Skin[/COLOR] to /usr/share/mplayer/[COLOR="Red"]skins/[/COLOR]
I just noticed that before I installed mplayer-skins I got a quick error window then nothing. I dont have the /skins/ folder. Only /Skin. I also get a font path error. Nothing about sound or video though.

---

### Post by ashrack on 2006-07-10
I tried moving the 'skins' to 'Skin' and the skin worked. So apperantly the new MPLAYER still supports the old Skin paths!
For the font problems U must install them:
[http://www.mplayerhq.hu/design7/dload.html#fonts](http://www.mplayerhq.hu/design7/dload.html#fonts)

ps. am just starting to compile to mozilla plugin for mplayer!! Will post it here if anybody is interested.

---

### Post by MetalMusicAddict on 2006-07-10
Thanx for being on so top of this ashrack. Would it be possiable to have a package that contains everything needed? ie: Fonts/skins and moz plugin?

What skins do you guys recommend? How do you get that borderless window?

Also for anyone using a widescreen monitor I couldnt find the config so I added **-monitoraspect 16:10** to the launcher and that fixed the aspect issue. ie: **gmplayer -monitoraspect 16:10**

EDIT: the config is the mostly empty file in ~/.mplayer/**config**. Not** mplayer.conf**

---

### Post by ashrack on 2006-07-10
am sure it is possible. but am still a rocky when it comes to compiling stuff. 
Anyway I have to start packing for holiday and Im having some grave difficulties with MPLAYER PLUGIN so I quess that will have to wait till I get home

---

### Post by gurgle on 2006-07-13
any word on a build for amd64? thanks :)

---

