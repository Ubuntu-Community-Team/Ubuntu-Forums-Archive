---
title: "avi's use 100% cpu"
date: 2006-02-20
forum: General Help
---

### Post by gooner on 2006-02-20
while trying to run any of my avi's i find that after around 10 minutes of play at default resolution (far less if i play the file in fullscreen mode) the video slows down, becomes choppy and  grinds to a halt whilst the cpu monitors shows a sharp increase in prosessor usage. usualy it goes from using around 30% to 100% in the space of 3 seconds where it stays. i've tried various media players, codecs and drivers and non play these files to an exceptable level.I am currently using the xv driver in xine to play my AVIs since it has the best performance but pauseing the video every 5 minutes for a minute or so before starting it again is unexceptable. thankyou in advance for any suggestions or solutions.

---

### Post by gooner on 2006-02-20
i just ran xine check and everything was marked as good apart from the following.

[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...

[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

---

