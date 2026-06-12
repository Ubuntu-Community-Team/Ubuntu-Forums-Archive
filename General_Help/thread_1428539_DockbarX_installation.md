---
title: "DockbarX installation"
date: 2010-03-12
forum: General Help
---

### Post by krapp on 2010-03-12
Hi--

I'm new to Linux and I'm trying to install DockbarX, and as I saw that the developer hangs around these parts, I'll post up to where I go in the Terminal:



What should I do?--how shall I proceed?

Thanks for the help.

---

### Post by krapp on 2010-03-13
It seems gnome-global-menu was preventing the DockbarX from appearing in my "Add to Panel" list; once I followed the instructions here [http://ubuntuforums.org/showthread.php?t=987341&highlight=gnome2-globalmenu](http://ubuntuforums.org/showthread.php?t=987341&highlight=gnome2-globalmenu) for disabling it, the DockbarX applet appeared. One question though; the applet all there's to it, correct? Aside from themes, etc., I'm not missing another essential component to this thing, am I?

---

### Post by krapp on 2010-03-13
And, on the same topic: I'm trying to move themes I downloaded to the themes folder, but Ubuntu says I don't have permission to do so, that I am not the "owner." Huh?

---

### Post by M7S on 2010-03-14
Yes, I hang around here (or rather I'm googling "dockbarx" on a daily basis to boost my ego ;) ).

And yes the applet is all there is to dockbarx. Though, if you use dockbarx to save screen real estate, you probably want to check out namebar as well.

The administrator is the owner of anything outside your home folder, that's why you can't copy your themes to /usr/share/dockbarx/themes without sudoing first. You can copy your themes to ~/.dockbarx/themes instead ("~" is short for your home folder).


M7S,
Dockbarx and Namebar developer

---

### Post by krapp on 2010-03-14
Thanks; but after doing that, and upon opening the dockbarx preferences, I got a blank window. I proceeded to log out thinking that might do the trick, but was instead subsequently stuck somewhere in between sessions (flickering grey text you see before the splash screen), and had to hard-reboot. Now, back in Ubuntu, I can add the dockbarx panel but no applications are appearing in it, preferences is once again a blank window, and I fear logging-out.

How do I completely uninstall dockbarx so as to install it cleanly? Or would that be unnecessary? Thanks; and great little applet you have here by the way.

---

### Post by M7S on 2010-03-15
I'm fairly sure it's not dockbarx's fault you get stuck between sessions. That sounds like some problems with graphics drivers or something.

If you open up a terminal and run "dockbarx run-in-window" and paste the error messages you get we can check what's wrong with dockbarx for you.

---

### Post by krapp on 2010-03-25
Writing back to note that I finally got dockbarx installed and working correctly, following partyboi's directions [http://ubuntuforums.org/showthread.php?t=1260680](http://ubuntuforums.org/showthread.php?t=1260680) with a little correction that pointed out a few posts down.

For themes and directions on how to install them I turned here [http://www.webupd8.org/2009/12/7-beautiful-dockbarx-themes-taskbar.html](http://www.webupd8.org/2009/12/7-beautiful-dockbarx-themes-taskbar.html).

Thanks for your help and time! And, again, thanks for this little program!

---

### Post by jazz_air_312 on 2010-09-11
Hi! i would like to uninstall dockbar x, the problem is that i didn't install it "the proper way" from the ppa, instead i installed from the setup.py (sudo ./setup.py install). Is there a way to completly remove it from my system?

---

