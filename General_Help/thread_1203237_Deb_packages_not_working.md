---
title: "Deb packages not working"
date: 2009-07-03
forum: General Help
---

### Post by AdmiralJonB on 2009-07-03
Hi

I just installed the netbook remix of 9.04 and for some reason it's not recognising .deb files at all for installation of a program, nor using deb to download one of them to install. Does anyone have any idea what's wrong/what could be done to fix this?

Thanks

---

### Post by coffeecat on 2009-07-03
Normallly, you can install .deb packages on NBR by double-clicking on them (or from the terminal) just like in regular Ubuntu. How exactly are you trying to install them? What .deb packages are they? Where did you get them? Can you install applications in the normal way from Add/Remove or Synaptic?

> **AdmiralJonB said:**
> nor using deb to download one of them to install.

I don't understand what you mean by this.

---

### Post by AdmiralJonB on 2009-07-03
Double-clicking on them doesn't work, it just asks me to choose which program to load it with. As for the second part, I mean something like "deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main". It just says deb is not a recognised command or something like that.

---

### Post by coffeecat on 2009-07-03
> **AdmiralJonB said:**
> Double-clicking on them doesn't work, it just asks me to choose which program to load it with.

If you right-click on a .deb file, does it offer you GDebi? If so, choose GDebi. GDebi should be the default app to open a .deb file, so if that's not happening you need to right-click > Properties > Open With and tick the box against GDebi. If GDebi isn't there, you must have uninstalled it somehow. Simply open Synaptic and reinstall GDebi.

> **AdmiralJonB said:**
> As for the second part, I mean something like "deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main".

"deb [http://akirad.cinelerra.org]("http://akirad.cinelerra.org/") akirad-jaunty main" sounds like a line that should go in your sources.list file. Where did you find that line? It should have given instructions on how to add to sources.list. Either edit /etc/apt/sources.list directly, or open Synaptic, go to Settings > Repositories > Third Party Software Tab. Now click on Add and add that line. Now click on Reload and you should be able to install cinelerra with Synaptic.

 > **AdmiralJonB said:**
> It just says deb is not a recognised command or something like that.

You're not trying to run that line from a terminal, are you? That won't do at all.

---

### Post by AdmiralJonB on 2009-07-03
> **coffeecat said:**
> 

"deb [http://akirad.cinelerra.org]("http://akirad.cinelerra.org/") akirad-jaunty main" sounds like a line that should go in your sources.list file. Where did you find that line? It should have given instructions on how to add to sources.list. Either edit /etc/apt/sources.list directly, or open Synaptic, go to Settings > Repositories > Third Party Software Tab. Now click on Add and add that line. Now click on Reload and you should be able to install cinelerra with Synaptic.

 

You're not trying to run that line from a terminal, are you? That won't do at all.

Now I feel embarrassed :S you're right with that one. It's been a while since I used ubuntu and I forgot. *slaps self*

gdebi isn't on the list however it is definitely installed. I used a terminal to install one file using it and it's in synaptic. I reinstalled it as well with no luck.

---

### Post by coffeecat on 2009-07-03
> **AdmiralJonB said:**
> gdebi isn't on the list however it is definitely installed. I used a terminal to install one file using it and it's in synaptic. I reinstalled it as well with no luck.

I don't know whether this will work, but try this.

Right-click on a .deb file and select Properties. Now the 'Open With' tab. Click on the Add button. At the bottom of the new window, drop the 'Use a custom command' pointer down and type 'gdebi' (no quotes) in the field. Click the Add button. Hopefully, you'll now have gdebi as an option for .deb files.

But hang on a minute. You're wanting to run cinelerra on a netbook? :shock: You must have the patience of Job. :p

---

