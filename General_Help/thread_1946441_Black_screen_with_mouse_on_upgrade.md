---
title: "Black screen with mouse on upgrade"
date: 2012-03-24
forum: General Help
---

### Post by Bardwise on 2012-03-24
I upgraded on ubuntu 10.04 yesterday and now, when I login at the terminal (I have never used the graphical login manager) I am presented with a black screen with a mouse.

I can run programs by pressing the terminal shortcut and running them from the terminal, but there is no visible desktop whatsoever.  The fonts are a bit strange, but programs, hotkeys etc function normally.

How do I get gnome back?

EDIT: Hmm, looks like the upgrade broke my gnome-panel package.  I reinstalled ran gnome-panel from the terminal and it works, but looks weird (gray instead of normal colours, some applets not appearing).  Any ideas?

---

### Post by imachavel on 2012-03-24
I am not understanding, you say from grub you select terminal mode instead of allowing the gui to load? Well then how did you know gnome wasn't working? So you want to uninstall and reinstall gnome? Well load the gui from grub, but instead of logging in, hit the arrow down button, or the tool looking button, and select Ubuntu instead of gnome. This will load the unity compiz plug in interface instead of gnome. Once you get to the interface, maybe you can uninstall and reinstall gnome again. Sorry your updates screwed up gnome loading

so from the terminal line, if you can't get into ubuntu unity for some reason, this is what you used?

sudo apt-get uninstall gnome(version etc.)

sudo apt-get install gnome(version etc.)

and then sudo apt-get update

sudo apt-get upgrade?

Have you tried repeating the process but using those commands in a different order, seeing if it effects anything?

Just out of curiosity, just to make sure all the internet connectivity works in terminal mode, what does

ifconfig

or ping ubuntu.com

or 
[B]ifconfig -a | grep eth

or

[/B][B]sudo lshw -class network

give you? Well, you won't be able to paste it here since you'll be in terminal shell interface user mode
but, take a note of it everything runs well?
[/B]

---

