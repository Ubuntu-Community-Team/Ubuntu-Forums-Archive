---
title: "Installing Kubuntu Desktop Screws Up Fonts in Mozilla &amp; OO"
date: 2010-10-15
forum: General Help
---

### Post by neu5eeCh on 2010-10-15
Hi Folks,

After I installed the Kubuntu Desktop, my font rendering in Mozilla (Firefox and Thunderbird) died an ugly death (the new Ubuntu Font & others). Interestingly, the same problem besets OOo on the Kubuntu side - making the software extremely unpleasant to use.

So... the bug is easy to reproduce. Just install Kubuntu. 

Uninstalling doesn't help.

For those who want to forgo ruining their Mozilla experience, below is the Bug: 

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/654144](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/654144)

I'm offering this up to the community in the hopes some of you might have the hackery to solve this Bug? A Kubuntu setting, somewhere along the line, is messing with Gnome.

---

### Post by neu5eeCh on 2010-10-15
OK, this problem is *sort of* Solved. KDE installs a ~/.fonts.conf file in ones home directory. For some reason (I'm not a hacker) this file completely mucks up fonts in both Gnome and Kubuntu. Deleting or renaming the file solves the problem on the Gnome side.

If one logs back into Kubuntu, KDE will stubbornly reconstitute the .fonts/conf file. 

That's too bad, because both Gnome and Kubuntu render correctly without it - the file itself is the bug? In general, Kubuntu's fonts are too small, but that's a separate issue (I think). 

So, the solution is twofold: 1.) Delete or rename ~./fonts.config 2.) Don't log back into or "use" Kubuntu. That's the best that I can do until canonical comes up with a solution.

---

### Post by SeijiSensei on 2010-10-16
Go to System Settings > Application Appearance > GTK+ Appearance.  If you switch from QtCurve to Raleigh, you can change the fonts that applications like Firefox and OO use.  Personally I like QtCurve, but YMMV.

You can also try changing to the GTK+ style in the Style dialog of Application Appearance, though that will affect all applications, not just those that use the GTK+ engine like Firefox.

---

