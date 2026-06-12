---
title: "Natty 11.04 without Unity"
date: 2011-04-29
forum: General Help
---

### Post by winchendonsprings on 2011-04-29
I would like to upgrade one machine and install from scratch, 11.04, without the Unity interface.

I know it is possible to not use Unity by choosing the regular gnome desktop at log in, but is it possible to upgrade without Unity at all? I have a pretty stripped down version of Ubuntu 10.10 and I have tried Unity 3d as well as 2d in virtual machines for a couple months. It's not for me.

Possible?

---

### Post by indus_credo on 2011-04-29
Same question here. I understand that I can change to Classic but what if I don't want to install it at all. Or, if there isn't any such way, how can Unity be completely removed after a fresh installation.

([winchendonsprings]("http://ubuntuforums.org/member.php?u=852862"), I hope I am not spamming your thread)
:)

---

### Post by winchendonsprings on 2011-04-29
>  I hope I am not spamming your thread
Not at all.

I'm sure there are lots of people interested in this. I did a few searches and found a few similar solutions that didn't do exactly what I wanted. Like, install the server version then install a desktop environment, but you have to replace the server kernel with the desktop one. 

Anyway, I don't want Unity. Anyone have any tips?

---

### Post by krupintupple on 2011-04-29
I installed a beta a few weeks ago and was disappointed with Unity, so I attempted to swap it for Gnome, but had little success. I've found that, at least for this stage in the game, it's best to just ignore Unity and opt to start in "Classic Mode" which is mostly everything Gnome.

Although, it does irk me that there's all of that space being occupied by a program that I never consciously plan on running....

---

### Post by jerome1232 on 2011-04-29
note that Unity is still gnome. It's just a shell for gnome, like gnome-shell and gnome-panel (gnome-panel is that classic gnome look)


Anyways You could probably use an alternate install to get a core Ubuntu system (cli only) Install gnome-core and build up from there installing the applications you want.

---

### Post by mc4man on 2011-04-29
Unity is just _two_ of  a few dozen  compiz plugins, several  supporting libraries and a few misc. files (a whopping  3 MB or so. 
Does nothing if it's not enabled - but if you still wish to get completely  rid of
```
sudo apt-get purge libunity-misc0  unity unity-asset-pool \
unity-common unity-place-applications unity-place-files

```

That will leave 1 file  - libunity4, get rid of that you'll loss empathy and the evolution app indicator, your choice

You'd be just fine leaving it and not using.

---

### Post by Hedgehog1 on 2011-04-29
You can run Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

