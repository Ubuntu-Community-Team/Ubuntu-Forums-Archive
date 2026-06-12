---
title: "SDLMAME Freezes on exit"
date: 2009-11-01
forum: General Help
---

### Post by Silas (son of Silas) on 2009-11-01
For a few months now I have struggled with 3 separate Ubuntu desktops running SDLMAME that all refused to cleanly exit SDLMAME when I hit escape. Problem solved

If SDLMAME freezes, hangs, crashes or pauses when you try to exit SDLMAME or at all.. fire up a terminal and type:

>  
sudo apt-get install libsdl1.2debian-pulseaudioThis worked for all three of my Ubuntu boxes running Hardy, Intrepid and Karmic.

Edited to add: This also solved freezing of SDLMAME on my new 64-Bit Karmic build Arcade cab too.

Edited again to add:
This also works for MAME 0.136u1 and newer on Linux. As of 0.136u1 SDLMAME became part of the main MAME release and is no longer a separate offshoot.

---

### Post by captive on 2009-11-03
You are my hero of the day! :)
Thank you, it worked for me on my karmic

---

### Post by Cygoku on 2009-11-03
My hero aswell !! 

Cygoku

---

### Post by Silas (son of Silas) on 2009-11-04
I'm glad to have been of help.

For months I have thought I was going crazy. I had multiple machines all with exactly the same symptom yet whenever I searched the web I seemed to be the only person on the whole planet suffering with this.

I even considered running my arcade cabinet on XP if I couldn't get this sorted... shudder!

---

### Post by SpearZ on 2009-11-13
Recently installed Karmic (9.10) and saw GMAMEUI in the repo's.  Installed it and gave it a go, but I had no sound and it completely froze the screen on exit each time (even with Compiz turned off).
The solution in this thread gave me sound in my MAME games, and also stopped the screen from freezing!  Thanks a lot!
I would be lost without ubuntuforums and generous posters :-)))

---

### Post by uowmag on 2010-01-18
Can I also add my thanks and congratulations for solving this.

---

### Post by Silas (son of Silas) on 2010-01-18
> **uowmag said:**
> Can I also add my thanks and congratulations for solving this.

You are more than welcome!

---

### Post by hulkntyger on 2010-02-15
After trying many ideas, I finally read this post.  This trick worked for me too.  However, the sound is really choppy.  Is there a way to smooth it out a little?  Thanx!

---

### Post by Silas (son of Silas) on 2010-02-15
So let's break this down.

* What games does it sound choppy on, is it all games or just some?

* Are you running with a front end or from a terminal?

* Can you run a choppy sounding game from a terminal and tell me what the game is and what the frame rate is? (it should tell you after you exit the game)

* Have you tried running it at different samplerates? For example > sdlmame -sr 11025 pacman

---

### Post by hulkntyger on 2010-02-15
I was running Metal Slug 3 using a front end (GMAMEUI).  I tried running it from the terminal but it gives me file not found messages for every file, including the .bin files.  This happens even when I am in the correct directory.  The options I have set under GMAMEUI are as follows:
Display
Video Mode:  Software
checked Run in Window; checked Keep aspect ratio; checked Reduce tearing effects, and checked Horizontal and Vertical centre.  Unchecked maximize; unchecked Allow uneven stretching
 
OpenGL
Checked filter (bilinear filtering, prescale 1); checked enable OpenGL VBO and enable OpenGL GLSL, Checked Let GLSL handle brightness and contrast;  Also No filter is selected
 
Sound
Checked Enable samples.  Rate set at 44100. Audio latency 2.  (I tried setting the other rates, but they created annoying popping and crackling during gameplay.)
 
Performance
Checked Automatic framskip; Checked refresh speed; checked Enable multithreading.  Speed set to 1.

---

### Post by Silas (son of Silas) on 2010-02-16
OK.... Lets rule GMAMEUI out of the equation.

From a terminal type:
>  sudo gedit /etc/sdlmame/mame.iniIf your mame.ini is in a different location, modify the line above accordingly.

In the first section of your mame.ini file  find the section that starts > # CORE SEARCH PATH OPTIONS modify the path locations to exactly match the locations of your ROMs.

The easiest method of doing that is to browse to the folder you keep your ROMs in then right click on a ROM file and click properties. Select and copy the 'Location' displayed on the properties tab and past it into your mame.ini

When you've saved the mame.ini try running Metal Slug 3 directly from the terminal again by typing > sdlmame mslug3 The key is to get SDLMAME running correctly in its own right first, thereby allowing us to identify if the issue is the front end or SDLMAME itself.

When you exit the game, copy and past the output from your terminal into this thread. It should look like this:

> 
silas@silas_pc:~$ sdlmame mslug3
Average speed: 100.00% (14 seconds)



From my experience with front ends its often not SDLMAME causing issues but The front end itself. (Except WAH!CADE, which has never caused me any issues)

---

### Post by sedawk on 2010-02-18
Thankx!

I have similar problems with many other applications, e.g.
(AFAIR) hatari (Atari ST emulator), UAE (Amiga Emulator),
x64 (part of the "vice" commodore emulator).
They all seem to have some sound issues and all of them
need some killing via pkill -9 hatari/x64/...

I will give it a try this evening ...

Thankx!

---

### Post by dphirschler on 2010-02-22
This worked for me.  Thanks.  Sound is still a little crackly, but not too bad.


Darryl

---

