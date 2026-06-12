---
title: "Has anyone got FreeOrion to compile in Natty or Precise?"
date: 2012-05-02
forum: General Help
---

### Post by shadowfirebird on 2012-05-02
Hi,  I fancied playing [FreeOrion]("http://freeorion.org/index.php/Compile_In_Linux") but the only way to get it working appears to be to compile it.

I'm game, but there are a LOT of dependancies, it uses cmake, and the instructions for the build appear to be out of date (they don't match the tarball).

Has anyone got it working in either Natty or Precise?  If so, how?

Or, can anyone recommend another turn-based, conquor-the-universe game that is easier to get going?

Ta.

---

### Post by milosz.galazka on 2012-05-02
Hello, 
I play Master of Orion 1/2, Alpha Centauri using wine, got them on Good Old Games. 

For games with easy to install packages you can check [playdeb.net]("http://www.playdeb.net/software/UFO%20Alien%20Invasion").

---

### Post by PeterP24 on 2012-05-02
I just went to freeorion sourceforge page and took a version for linux FreeOrion-0.3.15-Linux-i386.tar.gz which may not be the latest one. In order to install it, the only thing I had to do was to run ./setup.sh in the unpacked folder of the game. Now I have it up and running. I had already all the dependencies installed (because I like to go to github and test the latest version of various games - like naev or pioneer space sim). FYI - there is a clone of Master of Orion for Linux, named OpenMOO2 - but it requires you to have the original game (in order to use the original game data files). Freeorion claims not to be a clone, but inspired by the MOO series - which is nice.

---

### Post by shadowfirebird on 2012-05-03
Well, that's certainly a massive improvement, thank you!

I did as you did, downloaded the same version and ran setup.sh.  It installed perfectly.

But it segfaults when I run it; the only other message I see on the command line is that Python2.5 is missing and it's using the installed version.

Ah well.

---

### Post by PeterP24 on 2012-05-03
Sorry to hear that - I already have Python 2.5 installed (I needed it to run a version of Google App Engine) along Python 2.7 and 3.2 versions. It worked for me - I can play the game. You can install Python 2.5 as well - if this was the problem. Anyway, the README hints to a latest.tar.gz file for Linux which supposedly represent the latest snapshot for Linux. I wasn't able to find it on the website but I didn't search for it very much. You can contact the developers and ask for it. I would like to know how it turns out - thank you.

---

### Post by shadowfirebird on 2012-05-04
The bad news is that installing Python 2.5 makes no difference.  In fact on looking closer Python is actually shipped as part of that tarball; that's what the message is about.

The good news is that I've gone with plan B and am now playing the original Moo2 in dosbox.  Dosbox is soooo much easier to get working than wine; if you can lay your hands on the original files -- as I was lucky enough to be able to do -- I recommend it highly.

---

