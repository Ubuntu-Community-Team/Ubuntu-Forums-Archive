---
title: "Tar Files"
date: 2009-10-16
forum: General Help
---

### Post by cowboy7305 on 2009-10-16
Why is it so hard to install tar files in ubuntu ,iam trying to load Amarok2.2 at present and its a nightmare,i have had to look at half the net to get info about doing it using terminal, i really have never come to terms with this idea that an update does not load, there seems to me a lot of programs out there that are tar files  why cant we have a loader for them,from what i have seen on the forum ,and i have used it and had great advice ,a hell of a lot of people out there have no idea how to use the terminal and a hell of a lot like me never really want to
Go back to windows i hear or will read ,answer to that i don't want to 
I like Ubuntu but please make it easier to load programs  that are not in the system as  a deb file
Thats my Bitch

---

### Post by Rocket2DMn on 2009-10-16
Amarok2 is available in the repositories in Jaunty, you don't need to manually install it.  In fact, most applications that you will ever want are in the repositories.  You should be able to install it from Synaptic, or in terminal (assuming you are using Jaunty):
```
sudo apt-get install amarok
```

---

### Post by dcraven on 2009-10-17
I could very well be wrong in this particular case, but typically tarballs contain source code that needs to be compiled prior to "loading". This is the nature of an open source environment I suppose. First and foremost, projects make their source code available in source tarballs. To get a precompiled binary that you can "load" in your distro of choice is often a bonus excluding the ones found in your package manager.

Cheers,
~djc

---

