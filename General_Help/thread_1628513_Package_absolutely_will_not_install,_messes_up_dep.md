---
title: "Package absolutely will not install, messes up dependencies."
date: 2010-11-22
forum: General Help
---

### Post by Vitruvian Bacon on 2010-11-22
Hey everybody.

Having a minor problem. I'm trying to install the SDL_net library, known in Synaptic as libsdl-net1.2 

A little bit of background so I can give as much information as possible. I tried to install this the other day while trying to get AlephOne to compile. I could not find it initially under the repository (I guess I wasn't looking hard enough), so I tracked down an .rpm from the lib's website and installed it with alien. 

It didn't seem to install properly though, as AlephOne still lists it as a missing dependency, and when I tried download Doomsday from the Ubuntu Software center, it listed libsdl-net as a missing dependency and ground everything to a halt. I have since found it on the repository, but when I try to install it with Synaptic I get this error message:


E: /var/cache/apt/archives/libsdl-net1.2_1.2.7-2_i386.deb: trying to overwrite directory '/usr/lib/libSDL_net-1.2.so.0.0.7' in package sdl-net 1.2.7-2 with nondirectory

When I try to install it with apt I get this error:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

What should I do?

Edit:

I am running Xubuntu 10.10 on an Acer Aspire One.

Thank you so much in advance for your help.
~Vitruvian Bacon

---

