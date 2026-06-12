---
title: "remove black arrow from ubuntu drop down menu"
date: 2011-03-26
forum: General Help
---

### Post by bitbomb on 2011-03-26
Hi there,

I'm currently tweaking ubuntu to my liking.  I got rid of the "menu bar" and replaced it with the "Main Menu".  I don't like the black arrow on the Main Menu so I followed the instructions to get rid of it [posted here]("http://ubuntuforums.org/showthread.php?t=733808")

I got to the part where I type "sudo make"  However, I get the exact error [posted here]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/655205")

I tried to follow the solution, I installed libpanel-applet2-dev using synaptic.  I tried to edit the "Makefile" in the directory /var/cache/apt-build/build/gnome-panel-2.30.2.  However, when I opened this make file I did not find any line called
panel-compatibility.$(OBJEXT) panel.$(OBJEXT) applet.$(OBJEXT) \

Does anyone have any suggestions?  Thanks.

---

### Post by Krytarik on 2011-03-26
You could simply *hide* any of those arrows by modifying the theme you are using. Grab a copy of one of my themes and check out the file "THEME/gtk-2.0/panel.rc". Then try to apply it to your own theme, should be fairly easy.

Greetings.

---

### Post by bitbomb on 2011-03-27
I hadn't thought of that.  Thank you for the suggestion.  I'll play around with different themes.  However, I do prefer the theme I already have, so I'd really like to figure this problem out.

---

### Post by Krytarik on 2011-03-27
Like I said, it should be easy to apply that to your theme. At least much easier than compiling a custom gnome-panel. ;-)

---

