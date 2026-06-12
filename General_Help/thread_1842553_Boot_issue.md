---
title: "Boot issue"
date: 2011-09-11
forum: General Help
---

### Post by ratant on 2011-09-11
First things first: im on a cell phone, so searching the forums for this issue got tiresome really fast, and i have no other computer access. Using natty (11.04) 64 bit. Just downloaded and installed nvidia driver 280.13, hoping it would allow me to run the game Rift. tried to reboot once finished and I get a black screen with a list of tests each with [ ok ] next to them. When I type it produces strange character combinations, and it seems there is no way to leave this screen. When I enter tty and initially tried startx, it said there was a compatibility error of some sort. I tried reinstalling the driver (cd ~/downloads, sudo sh ./NVIDIA-Linux-x86_64-280.13.run), and now when I boot up instead of getting the list of ok'd tasks I'm just getting a black screen with a placemarker, and when I tried again to startx from tty it brings me to a fully black screen, no marker. Entered tty and there was a long list of 'no protocol specified' then xinit: giving up, unable to connect to x server. I noticed every time I tried Installing the driver a box popped up about failing pre-script something or other. At this point I just want to get to my desktop! I could care less whether or not I ever get to play rift, I just want to see my login and home screen again.

---

### Post by Rubi1200 on 2011-09-11
Hi and welcome to the forums :-)

Try passing boot options:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Start with nomodeset and let us know if this helps.

Also, have you tried recovery mode or an older kernel?

---

### Post by ratant on 2011-09-12
That nomodeset seems, from reading the description, like it would have helped. However, I ended up figuring out how to manually get rid of the newly installed driver altogether, so that I'm now back at a previous version. I think I deleted something else that is essential though, as now Unity is not working, and I'm forced to work through classic mode. This in itself isn't really a problem per se, but I would like Unity back. And honestly, I would still like to try and play Rift, which I know is possible, if I can just figure out what I need to do to make driver installation successful. I think that the problem lies in one of two areas essentially. 
       One, since my symptoms were pretty much identical to what is described in your link, possibly being the Plymouth issue (I have no idea what Plymouth is, by the way). The other, which I'm pretty sure needs to be addressed based on the error messages I was getting yesterday, is that when I install a new driver, certain vital files aren't being added to the proper directory which should be. I've read elsewhere that replacing kernels manually is necessary. (I won't pretend to know any of the inherent properties of kernels; they are just mysterious files to me) I just want to be sure that's the problem before I go deleting items I don't need to. Since I'm not extraordinarily computer-savy you could say, I'm apprehensive about such tasks. When I arrive at my Nvidia folder there are at least a dozen separate folders that have 'kernel' and/or 'current' in the title.
      Ideally, a step by step guide on how to upgrade my Nvidia drivers from my current 270.41.06 to something more recent, so that I can again run Unity, and perhaps Rift, would solve my problem. I feel like I may have all the pieces of the puzzel, they are just blurry and I don't know quite in which order to place them. I feel like if I tried right now to fix my problem, I'd probably just end up wrestling with a terminal and various boot menus for hours again, not getting where I need to be. Such is my level of noobdom.


EDIT: 
When trying the command unity --replace, an error message occurs, which seems related to something called 'opengl'. It says files are missing. By the way my card is a GeForce 7600 GT, in case that helps.

---

