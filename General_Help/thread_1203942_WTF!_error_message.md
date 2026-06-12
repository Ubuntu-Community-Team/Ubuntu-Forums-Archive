---
title: "WTF?! error message"
date: 2009-07-04
forum: General Help
---

### Post by Azmaedra on 2009-07-04
I have no clue what to make of this:

An error occurred

The following details are provided:

E: yiff-server: subprocess post-installation script returned error exit status 1

I get this message every time the update manager installs something, and I also got it while using the synaptic package manager to update a program called 'the battle for wesnoth'
If anyone has anything helpful to say please say it.
](*,)

---

### Post by synapsys on 2009-07-04
Try running:

```
sudo apt-get --reinstall install yiff-server
```

---

### Post by buffalojr on 2009-07-15
I was getting a similar problem. For some reason one of my dependencies kept messing up no matter what I did. The way I worked around it was to completely uninstall the program and then reinstall it using either a download or package manager (prefer package manager since it makes sure to get all the dependencies for you).

to uninstall (please note that this erases all game data, i.e. all the saved campaigns you have)

sudo aptitude purge wesnoth

then you can go reinstall the game from the add/remove applications and it should be fine.

---

