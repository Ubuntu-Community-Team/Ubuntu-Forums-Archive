---
title: "Have both Ubuntu and Kubuntu installed?"
date: 2010-10-21
forum: General Help
---

### Post by UnterUn on 2010-10-21
Hey! Strange problem, especially as i don't know why it's happened but I've managed to get both Kubuntu and Ubuntu installed :P ; it loads up under 'Kubuntu', then switches to 'Ubuntu' for login: the desktop too is the ubuntu style except i (had) doubles of all programs (Ubuntu and Kubuntu default) which i cleaned out, but i still have both sets of terminals. However that's not the problem: there's been a noticeable slowdown in the system and it just generally not working as it should. 

So any ideas how to fix this? :-k (By the way I'm using Ubuntu 10.10, 64 bit, and i have no idea what the kubuntu one is...)

---

### Post by spiky001 on 2010-10-21
Dont know what the problem with running slow is, Did you want both insalled? the difference between them both is the desktop Gnome Kde, it is possible to install both Gnome and Kde on 1 system of ubuntu and you can switch at login

---

### Post by UnterUn on 2010-10-21
> **spiky001 said:**
> Dont know what the problem with running slow is, Did you want both insalled?
err... no
> **spiky001 said:**
> The difference between them both is the desktop Gnome Kde, it is possible to install both Gnome and Kde on 1 system of ubuntu and you can switch at login

...I can't switch at login, i only have the choice of Ubuntu (and the standard recovery and that)... so i can only presume the Gnome and Kde arn't very happy with each other... anyway i did:
```
sudo apt-get remove kde*
sudo apt-get remove kubuntu*
sudo apt-get autoremove
```and it's seems to have speeded it up (but it still loads up in kubuntu)... and i have no idea *why* it would work but there was a problem somewhere in there

Thanks for the help! (Didn't realise kubuntu used kde)

---

### Post by StiltonSandwich on 2010-10-21
If you want to change the start up splash screen theme back to the Ubuntu one, you can remove the package *plymouth-theme-kubuntu-logo*.

Check that you have *plymouth-theme-ubuntu-logo* installed when you do this, otherwise you will have no splash screen, or a text-based one. It's perfectly fine not to have a splash screen, but you seem to want the Ubuntu one, so it's worth checking to make sure it's actually there!

(*Plymouth* is the program that displays the graphical splash screen while Ubuntu boots.)

Or, you can keep both splash screen themes installed and use the command
```
sudo update-alternatives --config default.plymouth
```
which should give you a choice between whichever splash themes are installed. Just type the appropriate number to choose one and press enter.

---

