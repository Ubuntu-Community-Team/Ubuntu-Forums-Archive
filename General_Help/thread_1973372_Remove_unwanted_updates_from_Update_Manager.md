---
title: "Remove unwanted updates from Update Manager?"
date: 2012-05-04
forum: General Help
---

### Post by Sith Lord Kyle on 2012-05-04
Been using 12.04 since beta, it's been pretty great... especially after removing Unity.  The only thing that I can't seem to figure out is some random updates in Update Manager.  Two specifically:  Synaptec touchpad update and Ubuntu examples.

I unselect them every time I do an update, but I'd like to just remove them altogether.  My computer doesn't even have a touchpad so it seems odd that'd be in there.  I don't know what the Ubuntu examples are, but I'm guessing I don't need them.

I almost thought to say "what the hell" and install them anyways but I figured I'd check to see if there was a way to rid of them first.

---

### Post by kc1di on 2012-05-04
heres a couple of this your should try:

In a terminal execute the following commands

```
sudo apt-get autoclean
```
```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```

---

### Post by 2ta8gdfte on 2012-05-04
> **Sith Lord Kyle said:**
> Been using 12.04 since beta, it's been pretty great... especially after removing Unity.  The only thing that I can't seem to figure out is some random updates in Update Manager.  Two specifically:  Synaptec touchpad update and Ubuntu examples.

I unselect them every time I do an update, but I'd like to just remove them altogether.  My computer doesn't even have a touchpad so it seems odd that'd be in there.  I don't know what the Ubuntu examples are, but I'm guessing I don't need them.

I almost thought to say "what the hell" and install them anyways but I figured I'd check to see if there was a way to rid of them first.

I think your over thinking things here possibly, apps have dependencies, for example the touchpad is part of the mouse control. You want to be careful with this is all I would say.

---

### Post by Sith Lord Kyle on 2012-05-06
> **2ta8gdfte said:**
> I think your over thinking things here possibly, apps have dependencies, for example the touchpad is part of the mouse control. You want to be careful with this is all I would say.

Ah, well, the touchpad thing seems okay then.  But I don't want Gwibber, I actually uninstalled it but Update Manager keeps trying to install the Facebook, Twitter, and other plugins for it even though it's gone.

---

### Post by Sith Lord Kyle on 2012-05-06
> **kc1di said:**
> heres a couple of this your should try:

In a terminal execute the following commands

```
sudo apt-get autoclean
```
```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```

Thanks for the code... but that didn't seem to have any effect.  Though it did seem to delete.... something.

---

### Post by Sith Lord Kyle on 2012-05-06
Well... I found the unwanted packages in Synaptic and removed them and they disappeared from my Update Manager.  So that's fixed.

However, now my Update Manage tells me I have a partially upgrade and need to install some stuff.  When I click that it gives me a list of things to install but they are all things I uninstalled on purpose.  Such as: sudoku, various game, Unity interface, etc.  I do not want any of that stuff installed.  Any way to get rid of the partial update thing?

If these are mandatory in 12.04, I may just go back to 10.04 or use a different distro.

---

