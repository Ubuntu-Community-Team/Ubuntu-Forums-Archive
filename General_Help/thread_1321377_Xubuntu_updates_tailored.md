---
title: "Xubuntu updates tailored?"
date: 2009-11-10
forum: General Help
---

### Post by krakenfury on 2009-11-10
I'm using Xubuntu Karmic pretty much as it comes. rt kernel and pulseaudio added. Both very smooth to switch to; thank you Ubuntu devs!
 
My question is: does the update manager tailor to my install? I assume that I'm safe to install any updates that show up there, but do I need all of them? I'm seeing stuff that's for Gnome and Nautilus today, so it makes me wonder if I'm getting the same set of updates as anyone using any flavor of Ubuntu, or if I'm only getting updates to packages I already have installed.

I understand that XFCE has some shared libraries and stuff with Gnome, but the Nautilus stuff is confusing me. I'm a VIKING, dernit. THUNAAAAAR!!

---

### Post by lloyd_b on 2009-11-10
I believe that the update manager is just a pretty front-end on top of the apt subsystem.  Which means it will only update the packages that would be updated if you had run "apt-get upgrade" at the command line.  This will NOT install any new package on your machine, unless something that you're upgrading is dependent on it.

There *are* a couple of "...gnome..." packages in a base Xubuntu install (I have three on my Xubuntu box), but nothing for nautilus, so I have no idea what packages you're updating.

Could you provide a little more info on the particular packages, specifically the package names?

Lloyd B.

Okay, I just did "sudo apt-get upgrade" on my machine (I don't use the update manager), and I got a "...nautilus..." package - It's a dependency of the "totem" package.

---

