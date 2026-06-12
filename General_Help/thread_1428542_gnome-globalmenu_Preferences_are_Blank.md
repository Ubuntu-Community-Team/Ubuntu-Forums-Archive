---
title: "gnome-globalmenu Preferences are Blank"
date: 2010-03-12
forum: General Help
---

### Post by Joseph Schwenker on 2010-03-12
I am using Ubuntu 9.10 x64, and I finally got gnome-globalmenu working!  Unfortunately, I am unable to edit its configurations using its "Preferences" menu, as I just have a big blank area where my preferences are supposed to be.  Is there a way to fix this, or a way to edit my preferences manually?  Thanks!  I am using gnome-applet-globalmenu 0.7.9.

---

### Post by Joseph Schwenker on 2010-03-12
After using the "Find" command in Gconf, I found /schemas/apps/gnome-applet-globalmenu/prefs/show_local_menu, and then "unset" a random key.  I was then able to use the preferences from the applet's right click menu.

---

### Post by krapp on 2010-03-12
Did you log-out and back in?

I am no longer using the menu but that worked for me. Unfortunately whatever was hindering the menu also nearly crashed Ubuntu when I tried to log-out; but after a hard reboot gnome-globalmenu seemed to work as it should, but leaving much to be desired, I would say. So now, seeing that the Mac way of doing things can't be replicated on Linux, I am trying to install what seems second best (the Windows 7 task bar!!!) in DockbarX but that is another story, another thread.

---

### Post by Joseph Schwenker on 2010-03-12
> **krapp said:**
> Did you log-out and back in?

I am no longer using the menu but that worked for me. Unfortunately whatever was hindering the menu also nearly crashed Ubuntu when I tried to log-out; but after a hard reboot gnome-globalmenu seemed to work as it should, but leaving much to be desired, I would say. So now, seeing that the Mac way of doing things can't be replicated on Linux, I am trying to install what seems second best (the Windows 7 task bar!!!) in DockbarX but that is another story, another thread.

Actually, the "Mac way of doing things" can be replicated in Ubuntu, and it gets better every day!  The Gloobus project currently aims to add coverflow and quickview support to Nautilus, and quickview is already perfectly stable.  Coverflow is coming soon.  I use Gnome-Do's Docky theme for a dock (it rocks!), and use Compiz's scale as my Expose imitation.  I never add anything for the sole purpose of imitation; I always add things that help my workflow.  I can't live without the scale plugin!

---

