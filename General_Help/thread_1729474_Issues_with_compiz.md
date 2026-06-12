---
title: "Issues with compiz"
date: 2011-04-15
forum: General Help
---

### Post by twtgd09 on 2011-04-15
Hey, I'm having some issues with getting compiz to work properly. I've installed it from the software center, but i dont think its loading right, because compositing / transparency is turned off, now my windows have little black lines and corners where there would typically be transparency. I can't figure out how to get this working again, whenever i open the ccsm thing, the title bars go away. Any help would be appreciated.

---

### Post by twtgd09 on 2011-04-15
I attempted to install cubeaddon through some means i dont remember, and now compiz doesnt work. I still have my gnome panels, but my cairo dock has a black box around it, and my windows all have a black / white / whatever colored stripe just above the title bar and forming a corner (presumably because transparency no longer works). Can any guide me through completely reinstalling compiz and getting it to work? or just fixing it?

---

### Post by twtgd09 on 2011-04-16
bump

---

### Post by Copper Bezel on 2011-04-16
1. Are you sure Compiz is running? It's obviously at least trying to launch, but check your System Monitor (in the main menu under Administration) to see whether or not it failed - the process will simply be listed as compiz. After that, try this: run the compiz --replace command from a terminal window and post any error messages you get here.

2. Your window decorations (frames) disappearing when you open ccsm is especially weird, because ccsm only configures Compiz - it won't start or end it.

---

### Post by twtgd09 on 2011-04-16
After reading some threads, i found that i can * mostly * fix my computers issues by selecting advanced desktop effects, however, compositing, as well as every other compiz plugin, is not working, and it used to. Whenever i check a box, and go away, the boxes are unchecked, all of them, in the compiz settings manager. Thoughts?

---

### Post by lisati on 2011-04-16
Merged, *Thread moved to **General Help**.*

---

### Post by K_45 on 2011-04-16
From here:

[http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html)

run this in a terminal

```
gconftool-2 --recursive-unset /apps/compiz
```

which restore the defaults and what was working before.

---

### Post by twtgd09 on 2011-04-16
Ran the recursive unset thing, typed compiz --replace, title bars are gone. I get hung up on "starting gtk window manager"
Selecting normal desktop effects results in the error message "could not enable desktop effects"

---

### Post by K_45 on 2011-04-16
What drivers are you running? The built in ones, the additional drivers, or the one's from ATI/Nvidia's website?

---

### Post by Copper Bezel on 2011-04-16
What Compiz packages do you have installed? It sounds like you might be missing a few - compiz-gnome, particularly, which explains the window decorations problem. Go to Administration -> Synaptic Package Manager and search for Compiz, then let us know what you have installed. Most of the little boxes should be green. = )

---

### Post by twtgd09 on 2011-04-16
[IMG]https://picasaweb.google.com/109829302212955261607/Apr162011?authkey=Gv1sRgCOaJz8TTiNDtKw#5596374080835434178[/IMG]
[IMG]https://picasaweb.google.com/109829302212955261607/Apr162011?authkey=Gv1sRgCOaJz8TTiNDtKw#5596374081331256018[/IMG]

---

### Post by Z06Gal on 2011-12-22
I am having the same issue.  I have tried compiz --replace, compiz-decorator --replace and compiz is still not running.  Everything is installed that should be but I cannot activate the windows decorator and still have the black box around my dock.  Any settings I put in ccsm, they never take effect and go away when I open ccsm again.  I have a Dell laptop with Intel integrated and Nvidia optimus and have it enabled via ironhide but nothing makes any difference in Gnome Classic [oneiric]. Anyone have any ideas? Thanks ;)


Robin

---

