---
title: "My games wont load."
date: 2009-12-20
forum: General Help
---

### Post by VendettaLord on 2009-12-20
First of all I just want to state, yes I do not know that much about ubtuntu, I am brand new to using ubuntu. Well first of all a few weeks ago my whole computer bugged up (something about my computer freezing in the middle of a system upgrade so it couldnt properly mount any of the drives) However that was seemingly fixed (as you can see I got it to turn on again by going and changing to 32 bit) now with the holidays upon us I had some extra time so I wanted to try my luck at a first person shooter (I was first trying open arena now i am trying tremulous). Unfortunately it wont even open and I have no idea what to do. Does anyone have any tips or suggestions? (please try to answer in simple terms I have very little knowledge of ubuntu).

---

### Post by Quarg on 2009-12-20
So, just to clarify... are you clicking on the game in a menu, and nothing happens? if so, try starting up a terminal (Applications>accesories>terminal) and typing in 
tremulous
and then posting the output. All this does is start the game in the console, and hopefully it will output any errors.

---

### Post by VendettaLord on 2009-12-20
OPENARENA
ioq3+oa 1.35 linux-i386 May  2 2009
----- FS_Startup -----
Current search path:
/home/dillon/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
4163 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 2.500
...setting mode 3: 640 480
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17



TREMULOUS 
tremulous 1.1.0 linux-x86 Sep  6 2008
----- FS_Startup -----
Current search path:
/home/dillon/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17

---

### Post by Kylerobhew1 on 2010-01-16
i am having a similar problem with a  few other games in Balazar Bros. i can get to the welcome screen but as soon as i try to start a new game it freezes up and my whole system freezes with it except for the mouse. i have tried using ctr+alt+f2 with no avail. i heard something about it being related to a conflict between soya3d and another app, if anyone can help me diagnose this it would be great, similar problem to this with openarena. i get as far as the animation at the beginning of the game and then it crashes and burns like Balazar Bros. both of these cause me to do a hard reset, i am new to ubuntu sorry if i'm posting in the wrong thread new to forums in general as well.

i'm using the latest intel drivers for my 945/gms onboard graphics card for whatever thats worth and a sound blaster live sound card

---

### Post by Abhijit Navale on 2010-01-16
I also have the very similar problems as u. In my case all this happend after messing up with SDL library files. I want to install Excalibur: Morgana’s Revenge v3.0. But it is not installing by itself. So somewhere i got info that i should first install and set SDL libraries. so from their web site i downloaded source package and install it. after that no 3d game is starting including, wideland,torcs, Balazar,Battle for Wasnoth. Someone should diagnos the problem with SDL libraries. let me know if anyone of u have some sort of solution or workaround.

---

### Post by Kylerobhew1 on 2010-01-18
i figured it out for me it was a faulty hdd, effin maxtor.

---

