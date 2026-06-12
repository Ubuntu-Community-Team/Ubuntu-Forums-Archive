---
title: "Hey all am new to ubuntu"
date: 2010-03-05
forum: General Help
---

### Post by Salue on 2010-03-05
Hey all i installed ubuntu on my desktop PC the 32bit one 
my specs are 
2.86 Quad Proccer 
4GB Ram
1GB VGA
1Tira Bite hard drive

those stats are from windows tho :P befor i formated it ;p
i got to know how to install amsn and to play mp3 on my ubuntu 

but like i wonder can you guys tell me how to make my ubuntu look cool like those youtube video's where like when they close the a window or a file it burns and like they have cube to move or what ever :P

and what are the games that would work on ubuntu =(

and what's the best MP3 player for ubuntu hope am not asking to much
and i hopei wrote this in the rite section ;p

---

### Post by Lucky. on 2010-03-05
Hey buddy!

Most of the fancy effects fall under "Compiz".  Compiz comes with Ubuntu, but you can't adjust it very well from the beginning.  In order to change all of the fancy settings (cube, flames, etc.), you will want to install "Advanced Desktop Effects Settings (ccsm) Compiz" from the "Ubuntu Software Center" or the "Synaptic Package Manager".

(I recommend the "Ubuntu Software Center".  Click "Applications", and it is at the bottom of the list.)

After installing this package, look under System->Preferences->CompizConfig Settings Manager.

The only tough part is that there are a TON of options to play with, and not all of them are straightforward.  Take your time and play around with them.  They're fun to tinker with!

If you find that you've messed the Compiz settings up too much and you'd like to go back to some standard settings, click on System->Preferences->Appearance.  Then click on the "Visual Effects" tab.  Selecting any of the three options ("None", "Normal", or "Extra") should reset your Compiz settings back to a more standard configuration.

As for games...

[This link](http://apcmag.com/top_5_best_free_open_source_games.htm) tells you about some nice games.  I think you can find all of those in the "Ubuntu Software Center" for easy installation.

[This link](http://en.wikipedia.org/wiki/List_of_open-source_video_games) shows you a list of tons of open source games.  Most of them work in Linux, and can also be found in "Ubuntu Software Center".

With some extra work, you can play [Dungeons & Dragons Online](http://www.ddo.com/playnow/), but it is a bit tricky.  It involves downloading the "Lord of the Rings Online" package, and getting it to work with DDO.  I've done it once with some help of some other forum people (do a search in Google, it will help), but it isn't as simple as other games.

You can play quite a few Windows games in Linux if you use WINE!  However it can be tricky and frustrating when things don't work perfectly.  It's kind of like a broken project car...you work and work and work on it, and it never seems to run.  But for some reason you keep working on it.  However I've played a number of Windows games in Linux.

If you like retrogaming, DOSBox also works great in Ubuntu.  Also ScummVM will help you play old LucasArts games.  These programs also work great in Windows, so they may be old news to you already.

[Quake Live](http://www.quakelive.com/) also works in Linux!

I've used Rhythmbox for MP3's, but I'm not too impressed with it.  If anybody else can suggest a better player, I'd be interested as well.

I hope you enjoy Ubuntu!  Take your time and see how you like it.  If you're feeling adventurous, try the 64 bit edition later on.  However it does seem to have trouble with Flash (you can get a 64 alpha/beta/something or other version), so 32 bit is a safer bet at times.

Good luck!

---

### Post by darolu on 2010-03-05
Hey, welcome to Ubuntu!

With that hardware you should use the 64-bit version, you won't be able to use all your 4GB of RAM with the 32-bit one.

To play mp3 and other proprietary formats install a package named "ubuntu-restricted-extras", go to System - Administration - Synaptic and look for it, you right click the box next to it to mark it for install.

You may want to install "sun-java6-jre" and "sun-java6-plugin" too.

I don't know if there is amsn in the regular repositories but you can try "emesene" is extremely similar to MSN messenger :p, go to Aplications - Software Center and look for it, other popular IM programs are Pidgin, Kopete and Empathy (the default one).

The cool effects you saw in youtube are enabled with "Compiz" (compositing program), it is installed by default, if you have ATI or Nvidia card, you may want to install the proprietary driver (System - Admin - Hardware Drivers); after that go to Synaptic and install "compizconfig-settings-manager" to have all the available effects, you can configure under system - preferences - compiz settings

With time, you'll discover there is no such thing as "the best" program (or whatever), what is "the best" for me, may not be "the best" for you, some people will tell you a command line player like mplayer is "the best" but you may find a GUI (graphical) program better. The default player (Rhythmbox) is very good, is what I use, other popular players are Amarok, Songbird and Exaile, if you like "winamp" you may want to try Audacious though.

About games, you won't find cutting-edge popular and new games in Linux, but we have options, there are a lot of great games for Linux, Open Arena, Secret Maryo Chronicles, No-gravity, Frozen-Buble, Yo Frankie! and Super Tux Kart are my personal favourites. You can run -some- Windows games using Wine (a windows emulator program) though, you may want to google for it.

---

### Post by rossmoore on 2010-03-05
I'm a fan of Banshee as a good music player - it's not perfect, but I feel it manages iPods and other MP3 players better than any of the alternatives. There's also Amarok (not many like the latest versions though), Exaile, Rhythmbox (the default) and Songbird as credible alternatives.

An OK FPS game that's free is Nexuiz, available in the repositories.

Let us know if you have trouble with Compiz - you may need to enable your "Restricted Drivers" for your graphics card.

---

### Post by Dayofswords on 2010-03-05
Nexuiz
[http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/)
i hear its a good game, my computer sucks so it doesnt work on mine but check it out, its in the software center

you need the ubuntu restricted extras for mp3's so you can even play them
open a terminal
**Applications** > **Accessories** > **Terminal** and type this in and provide your password
```
sudo apt-get install ubuntu-restricted-extras
```


get the Advanced Desktop Effects Settings (ccsm) that lucky mention, its great

for a media player, the defualt one works for me, as long as i can hear it, but there is songbird, its not in the center but you can a deb (like a exe installer but for debian based distros, like ubuntu)

---

### Post by rossmoore on 2010-03-05
Oh, good point about ubuntu-extras. Every time I install a fresh copy of Ubuntu I go straight to this post:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and run pretty much most of the sections here to set up music, flash, video, dvd playing etc.

---

### Post by Salue on 2010-03-05
hey thanks for the welcome and thanks for teching me some stuff i'll try them out but 
u guys said i should put unbuntu 64bit from where do i download it =( i tryed to get it from befor i couldnt find it =( can anyone give me the link

---

### Post by rossmoore on 2010-03-05
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Select "Alternative download options" and choose 64-bit.

---

### Post by Salue on 2010-03-05
Thanks alot bro =D downloading 
with my computer stats putting ubuntu 64bit will my pc be faster?

---

### Post by Malt Frisky on 2010-03-05
Welcome to Linux, another converted ;)

I heavily recommended Songbird as an alternative Itunes.

[http://www.getsongbird.com/](http://www.getsongbird.com/)

In fact I will say it's better than Itunes.

When you place your mp3 files in music folder it recongnises them straight away, you can change the skin, get lyrics and even guitar tabs as soon as you select a song.

Plus, you can sync it to last.fm finding artists biography, tickets selling in your area, videos, reviews, etc.

You won't be disappointed, heavy music listener, got about 32, 000 + songs and growing.

---

### Post by Salue on 2010-03-05
nice thanks i'' get them done after i finish downloadinig and installing ubuntu 64 bit xD

btw what is this super key i keep seeing like press Shift+super key what is super key='(

---

### Post by Dayofswords on 2010-03-05
> **Salue said:**
> 
my specs are 
2.86 Quad Proccer 
4GB Ram
1GB VGA
1Tira Bite hard drive


this is waaaayyy above any of my computers lol



not to pick at it but Terabyte is the proper spelling

---

### Post by Salue on 2010-03-05
haha thanks 
as for the spelling 
but atleast u got what i mean xD

---

### Post by produce101 on 2010-03-05
This is a great site. Am also new here, and I've already learn some new cool information. Nice meeting you, guys.

---

### Post by Salue on 2010-03-05
hey nice to meet you to bro 
ubuntu is extremly wierd to me i like formated it like 5times to make it work and 64bit didnt work for me =( it kept giving me error while installing it lol

---

### Post by QIII on 2010-03-05
Happy Ubuntuing!

Do you recall what the errors were when you attempted to install the 64 bit version?

There should have been no issues if your .iso image was burned correctly.

---

### Post by pricetech on 2010-03-05
> **Salue said:**
>  what is this super key i keep seeing like press Shift+super key what is super key='(

It's the one with the winders logo on it.  We don't call it the winders key here in Ubuntu land, lest tiny Penguins climb up out of our keyboards like armor plated cockroaches and consume us.

OK, just kidding about the Penguins, but it makes for an interesting mental picture doesn't it ?

---

### Post by Salue on 2010-03-05
funny XD but hey i need help =( i installed songbird
i dont know how to open it ='(
i cant find it in the application panal thing

---

### Post by Swagman on 2010-03-05
I would NOT recommend any linux N00b install 64 bit.

***FAR*** too much hassle for (arguably) little gain.

---

### Post by pricetech on 2010-03-05
I have to disagree.  The performance gain from 64 bit is well worth any grief it took to make a few problematic things work.

---

### Post by QIII on 2010-03-05
> **Swagman said:**
> I would NOT recommend any linux N00b install 64 bit.

***FAR*** too much hassle for (arguably) little gain.

Why?  There is much FUD flying about, but precious little in the way of substance.

Early on there may have been issues with 32 bit applications not working well.  64 bit Flash can still be a problem, but you can use 32 bit Flash.

There is substantial gain in any processor intensive tasks, such as video encoding and the like.

Of course, there is also the issue of memory addressing.  If you want to be able to use more than ~3.27GB of memory (you can't really even get all 4GB) you either have to enable PAE (and its performance hit) or a 64 bit OS.

The fact is that the entire industry, regardless of OS, has pretty much moved on from 32 bit OSes.  There were hangers-on in the transition from 8 to 16 and from 16 to 32.  Why let the world pass you by?  Why limit yourself to 32 bit applications when there are 64 bit applications aplenty?

There will always (well, for the foreseeable future) be a need for 32 bit OSes for those whose hardware architecture will not support 64 bit.

There are still people who use horses and buggies, too.

---

### Post by Dayofswords on 2010-03-08
> **Salue said:**
> funny XD but hey i need help =( i installed songbird
i dont know how to open it ='(
i cant find it in the application panal thing

how did you install it? 
if you used a deb it should be *Applications > Sound & video > Songbird*

---

