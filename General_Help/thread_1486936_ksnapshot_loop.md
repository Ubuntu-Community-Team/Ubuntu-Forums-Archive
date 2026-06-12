---
title: "ksnapshot loop"
date: 2010-05-18
forum: General Help
---

### Post by parallelothingy on 2010-05-18
Ok, first of all, I am basically a beginner in that I haven't had a lot of experience troubleshooting problems on my own, even though I've used various distros of Linux for about 5 years.  And this really isn't a beginner problem; more likely some kind of bug, I'm assuming.  Hope I picked the right forum.

I have no idea what brought this on, but every time I start up the GUI, ksnapshot opens and starts an endless loop, which I can only stop by switching to console or forcing shutdown with the power button.  "killall -9 ksnapshot" seems to do nothing, as the loop is still running when I switch back to GUI.  Is there any way to stop this so I can use the GUI again?  I read that uninstalling ksnapshot will still cause KDE to look for the program, thus not really solving anything, otherwise that would have been the first thing I would have tried.

Another way to go would be just to backup files onto my blackberry in command line before doing a fresh install.  Ive been meaning to upgrade to the most recent release anyway, and have been thinking about switching to lubuntu or xubuntu.  But is there something special I need to do to mount it since it's a blackberry and not a USB stick?  I tried [the instructions on the Ubuntu site for mounting a USB stick](https://help.ubuntu.com/community/Mount/USB), but when I try to mount the device, I get what looks like a man page on proper use of mount.  

Any help is appreciated, thanks!

---

### Post by gmargo on 2010-05-18
Two ideas, don't know if they'll help.  A lot less drastic than a reinstall though.

Level 1: Just rename the ksnapshot binary (to ksnapshot.save) for now.  Then you might be able to track down whoever is trying to run it.  Rename ksnapshot back later.

Level 2: Rename your $HOME/.kde directory to start fresh.  (I bet this will fix it.)

Of course you need to log out/in for both ideas.

---

