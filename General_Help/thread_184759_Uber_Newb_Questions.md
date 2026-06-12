---
title: "Uber Newb Questions"
date: 2006-05-30
forum: General Help
---

### Post by Dark Elitist on 2006-05-30
I am going to be installing Dapper on a friend's computer in about two weeks (I am converting a lot of people!) and was wondering if anything special needs to be done to add memory to a computer running Ubuntu or if it is all entirely automatic. He currently has 256 and will, when he can spare the cash, be upgrading to 768 by adding a 512 chip.

Also, how well will Dapper, combined with the latest nvidia drivers off of nvidia's website and a GeForce 3 DDR 64MB, run Doom 3 on low quality at 640x480 on a Pentium 4 1.6? I know that most id Software games run a lot better in Linux than Windows so I was wondering if it will be playable with little to no lag.

By the way, how is Dapper coming along? I have been reading the forums a bit and it seems as if there have been problems.

Alright, thanks everyone!

---

### Post by henriquemaia on 2006-05-30
[quote=Dark Elitist]I am going to be installing Dapper on a friend's computer in about two weeks (I am converting a lot of people!) and was wondering if anything special needs to be done to add memory to a computer running Ubuntu or if it is all entirely automatic. He currently has 256 and will, when he can spare the cash, be upgrading to 768 by adding a 512 chip.

Also, how well will Dapper, combined with the latest nvidia drivers off of nvidia's website and a GeForce 3 DDR 64MB, run Doom 3 on low quality at 640x480 on a Pentium 4 1.6? I know that most id Software games run a lot better in Linux than Windows so I was wondering if it will be playable with little to no lag.

By the way, how is Dapper coming along? I have been reading the forums a bit and it seems as if there have been problems.

About Dapper and how it is coming along, you will find different answers according to people's hardware. I have the Dapper 64bit version installed and I'm very happy with it.

Alright, thanks everyone![/quote] 
I'm not totaly aware of the technical issues of simply adding more memory to Ubuntu, but I have done that on other occasions and all went fine. I guess the only problem is if the swap partition is too small for the new setup, but someone more expert in these issues can explain this better.

About on how's Dapper coming along, you'll find different answers according to people's hardware. I have Dapper 64bit version and I'm very happy with it.

---

### Post by XAsmodeanX on 2006-05-30
It should automatically be updated as soon as you put it in the computer.  The bios will detect it and then when you start Ubuntu it shouldn't even blink at it.

As for Doom 3, I have no idea.  But, I do know that if you go with XGL/Compiz (the cool wobbly windows) you can pretty much count on not playing any GL games.

---

### Post by Dark Elitist on 2006-05-30
[QUOTE=XAsmodeanX]It should automatically be updated as soon as you put it in the computer.  The bios will detect it and then when you start Ubuntu it shouldn't even blink at it.

As for Doom 3, I have no idea.  But, I do know that if you go with XGL/Compiz (the cool wobbly windows) you can pretty much count on not playing any GL games.[/QUOTE]

I see. Thanks!

I was able to help a different friend get Doom 3 working on his 5.10 install. He has only a REGULAR PCI GeForce FX 5200 256MB and the game runs fine. I was kind of amazed because PCI graphics cards usually lag like mad in Windows, especially for games as complex as Doom 3. Linux truly is an amazing operating system but I am very curious as to whether or not it will be amazing enough to make Doom 3 purrr on a GeForce 3.

As always, thanks guys!

---

### Post by syntek on 2006-05-30
[QUOTE=XAsmodeanX]It should automatically be updated as soon as you put it in the computer.  The bios will detect it and then when you start Ubuntu it shouldn't even blink at it.

As for Doom 3, I have no idea.  But, I do know that if you go with XGL/Compiz (the cool wobbly windows) you can pretty much count on not playing any GL games.[/QUOTE]
that's not really true. ive got xgl/compiz running over here and have found workarounds to every xgl-related problem so far. although, some of my solutions are a bit cludgy.. for example:
GL games such as doom3 and unreal 2003 i simply spawn another xserver without xgl to run the game. i made a simple wrapper script so i just click on the game in my games menu and it does everything for me. when i close the game, it exits the xsession.
video playback works flawlessly with mplayer. totem works great playing every format aside from wmv's.. mplayer plays everything.
sdl games like supertux or frozen-bubble working fine if launched from the console with an export variable added to my .bashrc
and for anything else that i cant seem to get working (at the moment, only java programs) i fire up a nested xsession and launch whatever i need in there.

xgl rocks my socks.. ;)

---

### Post by JoWilly on 2006-05-30
[QUOTE=syntek]that's not really true. ive got xgl/compiz running over here and have found workarounds to every xgl-related problem so far. although, some of my solutions are a bit cludgy.. for example:
GL games such as doom3 and unreal 2003 i simply spawn another xserver without xgl to run the game. i made a simple wrapper script so i just click on the game in my games menu and it does everything for me. when i close the game, it exits the xsession.

xgl rocks my socks.. ;)[/QUOTE]

hehehe... nice :) 

Would you mind sharing your script ?

---

### Post by Lil_Eagle on 2006-05-30
If you upgrade the memory in the PC, the chances that the swap file will be needed will go down.  All the guides say to make the swap file twice the size of the memory, but most of those guides were written when 256 MB of memory was a lot.  In any modern computer with 512 or more, theoretically you don't need a swap file.  I wouldn't try not creating one though.  The kernel expects it.

The whole reason for the swap file is to off-load memory.  Think of it as Virtual Memory, as that's exactly how linux uses it.  The more real memory you have, the better, in just about all OS's.  (There are exceptions)

---

### Post by syntek on 2006-05-30
[QUOTE=JoWilly]hehehe... nice :) 

Would you mind sharing your script ?[/QUOTE]
sure, i found it here on the forums..
```
sudo gedit /usr/bin/Xgames
```
```
#!/bin/sh
X :1 -ac -br -config /etc/X11/xorg.conf.games &
export DISPLAY="localhost:1"
sleep 1
su [/b]syntek[/b] -c $1
sleep 1
kill `cat /tmp/.X1-lock`
```
make sure you change your username on the 5th line to reflect your system, then edit your menu entries for your openGL games to run, for example ut2004 to:
```
gksudo Xgames ut2004-bin
```

---

### Post by JoWilly on 2006-05-30
[QUOTE=Lil_Eagle]In any modern computer with 512 or more, theoretically you don't need a swap file.  I wouldn't try not creating one though.  The kernel expects it.
[/QUOTE]

I have been running my 1Gb system for 2 years with no swap. I never had any problem, and the advantage is that it never swaps ;) 

I have reinstalled dapper a few days ago with 512 Mb swap to see how it goes. After running for a few days it now uses 20 Mb swap.

So imho if you have 1GB+ and if you have no specific need for it (special intensive app or such), swap is not needed and you system will be faster as it will not write to the HD.

---

### Post by JoWilly on 2006-05-30
[QUOTE=syntek]sure, i found it here on the forums..
```
sudo gedit /usr/bin/Xgames
```
```
#!/bin/sh
X :1 -ac -br -config /etc/X11/xorg.conf.games &
export DISPLAY="localhost:1"
sleep 1
su [/b]syntek[/b] -c $1
sleep 1
kill `cat /tmp/.X1-lock`
```
make sure you change your username on the 5th line to reflect your system, then edit your menu entries for your openGL games to run, for example ut2004 to:
```
gksudo Xgames ut2004-bin
```[/QUOTE]

Looks great, thanks ! :D

---

### Post by XAsmodeanX on 2006-05-30
Couldn't get the script to run :/

---

### Post by slavik on 2006-05-30
the cluster that I am going to be helping set up has 4GB memory (6 systems with 4 CPUs) and 16GB swap.

---

