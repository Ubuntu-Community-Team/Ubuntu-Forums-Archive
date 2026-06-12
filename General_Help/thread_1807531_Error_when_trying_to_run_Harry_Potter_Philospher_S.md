---
title: "Error when trying to run Harry Potter Philospher Stone PC game with Wine"
date: 2011-07-19
forum: General Help
---

### Post by nilrezei on 2011-07-19
I have Ubuntu 11.04. My system exceeds by far the recommendations for the game. The game is from 2001 and has very low system specs, so that's not the problem. Other games run fine, I have 3d acceleration etc.

The game installs, but when I try to run it, it gives me the following error:

Critical Error:
General Protection Fault
History: UD3DRenderDevice::CreateVideoTexture <- AllocTextures <- UD3DRenderDevice:: SetRes <- UD3DRenderDevice::Init <- UWindowsViewport::TryRenderDevice <- UWindowsViewport::OpenWindow <-UGameEngine::Init <- InitEngine

I really love that game and couldn't do without it. I appreciate any help. Thank you.

P.S. Another problem, not games related. My Ubuntu desktop freezes completely sometimes if screen is idle for a few minutes. A blank, white full screen appears and nothing I do can get me back to normal desktop. Only solution is Restart.

---

### Post by nilrezei on 2011-07-21
Bump!

Come on, guys, any help here? I searched Wine forums and found similar problem, they say game's engine is suported and it has to be distro problem...

---

### Post by ronnielsen1 on 2011-07-21
Run winecfg in a terminal and make sure that emulate virtual desktop is checked under the graphics tab. Alternatively, try different windows versions under the applications tab

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=6511](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=6511)
>  	 		Selected Test Results (selected in 'Test Results' table below) 	
  **What works**
Installation, menu (no lags like in HP and chamber of secrets), moving, controlling by mouse and keyboard.      


**What does not**
Playing the game without "emulate virtual desktop".      


**What was not tested**
Quidditch, finishing the game 

**Additional Comments**

It needs "emulate virtual desktop" to run and game is sometimes too fast

 


> P.S. Another problem, not games related. My Ubuntu desktop freezes  completely sometimes if screen is idle for a few minutes. A blank, white  full screen appears and nothing I do can get me back to normal desktop.  Only solution is Restart. 	

Sounds like a hibernation issue. I usually adjust my Power Management settings under Screensaver to avoid turning off the hard drive, computer etc as I have had trouble with this also

---

### Post by nilrezei on 2011-07-25
> **ronnielsen1 said:**
> Run winecfg in a terminal and make sure that emulate virtual desktop is checked under the graphics tab. Alternatively, try different windows versions under the applications tab

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=6511](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=6511)




Sounds like a hibernation issue. I usually adjust my Power Management settings under Screensaver to avoid turning off the hard drive, computer etc as I have had trouble with this also

Well, I enabled virtual desktop in wine cfg, but that didn't change a thing from what I already accomplished before...

Before reading your post, I tried to run the game with different desktop resolutions. It seemed to work with 640x480, but only a bit. What do I mean by "a bit":

The game installs, but does not run at all without a game engine update. After engine update, it only starts if one chooses Software Rendering from game start window, when the game prompts you to choose between Direct3D and Software Rendering.

Then the game starts, the first cinematic, with the storyteller, then it crashes to desktop when is supposed to entry main room of Hogwarts. The game makes a save there, which appears in the save/load window, but if clicked, it crashes again.

I tried importing a different save from a Windows machine and same thing. Tried another save and it actually entered the game and was able to cast one spell :), then crashed to desktop again. Then it never worked at all, always crashes.

By the way, the game's sequel, "HP - Chamber of Secrets" runs very well, only if you run it from a 1024x768 native desktop resolution, otherwise it throws same error with "General Protection Fault"...

It seems to be a resolution problem after all, but I wonder why?! 

And what can be done for the game to properly run?

---

### Post by ronnielsen1 on 2011-07-26
Is this a shareware game or do you have a link for it? I'll give it a try to see if I can get it running.

---

### Post by nilrezei on 2011-07-26
> **ronnielsen1 said:**
> Is this a shareware game or do you have a link for it? I'll give it a try to see if I can get it running.

Well, the game is older, but it isn't free yet, unfortunately:
[http://en.wikipedia.org/wiki/Harry_Potter_and_the_Philosopher%27s_Stone_%28video_game%29](http://en.wikipedia.org/wiki/Harry_Potter_and_the_Philosopher%27s_Stone_%28video_game%29)

Which is a pity, it's only logical they made freeware any software older than 10 years...

Try the demo:
[http://www.gamesforum.ca/showthread.php?t=351679](http://www.gamesforum.ca/showthread.php?t=351679)

I'm confident the game will run, with some little tweaking. Otherwise, it wouldn't had even entered the game world, even for a few seconds, right? :D

---

### Post by Mark Phelps on 2011-07-26
The WineHQ site page for that game is linked below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4317]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4317")

Silver is a poor rating -- and you should read through the Test Results to see what other folks did.

---

### Post by nilrezei on 2011-07-27
> **Mark Phelps said:**
> The WineHQ site page for that game is linked below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4317](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4317)

Silver is a poor rating -- and you should read through the Test Results to see what other folks did.

Quote from your link:

> **What works**
Installation, menu (no lags like in HP and chamber of secrets), moving, controlling by mouse and keyboard.      


**What does not**
Playing the game without "emulate virtual desktop".      I do not even get to the point where I'm moving or controlling by mouse, keyboard etc !

Actually it's the same with or without "emulate virtual desktop", if you change desktop resolution. Simply emulating virtual desktop doesn't by itself make the game run.

What is really a puzzle is that the game's sequel runs very well, faster than in Windows even...

If the sequel is running, the first one should too. Same engine, same stuff. 10 years old and Linux/Wine can do nothing about it??

---

