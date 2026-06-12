---
title: "ubuntu 10.10  software installation problems"
date: 2010-12-29
forum: General Help
---

### Post by span22 on 2010-12-29
I'm rather new to ubuntu/linux and I've run into a bit of a hiccup, any time I try to install software from the ubuntu software center I get the following message 

> The action would require the installation of packages from not authenticated sources.

and it refuses to download the software. It gives this message no matter what I try to install.

---

### Post by walruspanzer on 2010-12-29
Did you try using synaptic package manager?

---

### Post by span22 on 2010-12-30
synaptic is still giving me error messages unfortunately

---

### Post by mcduck on 2010-12-30
> **span22 said:**
> I'm rather new to ubuntu/linux and I've run into a bit of a hiccup, any time I try to install software from the ubuntu software center I get the following message 



and it refuses to download the software. It gives this message no matter what I try to install.

hat is pretty much always a result from adding some third-party software rpository, nbut not adding the authentication key for it.

As a result the software is available but the downlaoded fles can't be checked for authenticity, and you get a warnign about it every time you use the package manager.

It shouldn't stop you from installing anything, though, it's just a warning. But you really should add the missing authentication key anyway. Which ever repository you have recently enabled, they should have instructions for adding the key on their web site.

---

### Post by span22 on 2011-01-02
And where do I add this key? The terminal? Like I said I'm new to this OS so you'll have to spell it out for me I'm afraid

---

### Post by Vigh on 2011-01-02
system -> administration -> synaptic package manage -> settings -> repositories -> software sources -> other software, will show you your non-official software sources, not sure about how to fix your problem though, i had the same problem and just deleted the ppa's from other software

---

### Post by mcduck on 2011-01-02
> **span22 said:**
> And where do I add this key? The terminal? Like I said I'm new to this OS so you'll have to spell it out for me I'm afraid

You should find both the key and instructions for importing it on the same place where you got the address for the repository itself.

Foe example every PPA repository has the key available that way, and there's also a link to instructions for adding the repository and the key (just click the "Read about installing"-link).

But when it comes to PPA repositories, if you are running Ubuntu 9.10 or later you should juts use the "*add-apt-repository*" command to add it, as it will at the same time add the repository to your sources and automatically import the key for you.

For example to add the [gnome-colors PPA repository]("https://launchpad.net/~gnome-colors-packagers/+archive/ppa") you'd open a terminal and run "*sudo add-apt-repository ppa:gnome-colors-packagers/ppa*"

---

### Post by chuzzle44 on 2011-01-03
If this hasn't been fixed yet:
I had the same problem.  I was told to enter  "sudo apt-get update"  into Terminal.
(Without quotes of course)  This has worked well for me in both the desktop and the netbook editions. I hope it works for you.

---

