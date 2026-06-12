---
title: "Ubuntu 11.10 Application Buttons Not Working"
date: 2011-10-14
forum: General Help
---

### Post by cookacounty on 2011-10-14
I just updated to Ubuntu 11.10 from 11.04 and suddenly the form buttons for Cadence 5.1 have stopped working (For example when a dialog pops up giving a warning I click OK and nothing happens)! 
There not much more info I can provide other than strangely, when I move the window the button will respond. I am able to hit enter and the button also works.

On other notes, I found my nautilus was constantly crashing until I removed the launch terminal plugin.

If anyone has some ideas, I would gladly try them.

Thanks in advance!

---

### Post by john_ferrier on 2011-10-21
I have similar problem with Ubuntu with unity3D. I compiled a text editor called "nedit" with Openmotif and found the some of the dialog button not working (no response when clicking on them). However, if I ran the same compiled binary executable on Unity2D or Gnome there was not a problem at all. I did the same thing on Ubuntu 11.04 and there was not a problem for Unity3D. So the conclusion is from 11.04->11.10 something was broken.

---

### Post by kaizen666 on 2011-10-23
Just got here from google, so sorry if its already been fixed, but I am also having a problem with the sidebar of Unity.  When I click for applications to work, it's a bit of a lottery and it feels like similar odds to winning the lottery and an application actually opening.

Is there something I need to add or do to get the apps to load when I click on them? I also cannot right click them and create desktop icons either now, so I just have whatever is currently in my sidebar/on my desktop working correctly.

oh, and I'm also on 11.10 now but for some reason I no longer have privileges to correct my details.

---

### Post by john_ferrier on 2011-10-30
I believe my problem was caused by bugs newly introduced in the latest Unity. Unfortunately Canonical and/or Ubuntu developers are more caring fancy graphic interfaces rather than the core of the system.

---

### Post by bgreat on 2012-02-15
The problem was with the compiz package used by Unity 3D. Unity 2D does not exhibit the issue. As of 14-Feb-2012 the issue has been corrected. If you can update to the current fixed versions from a terminal window by doing:

sudo apt-get update
sudo apt-get upgrade

Or use the graphical "Update Manager" to install the latest versions.

You can get more information on the Ubuntu web site under: [Bug #890947]("https://bugs.launchpad.net/compiz-core/+bug/890947")

---

