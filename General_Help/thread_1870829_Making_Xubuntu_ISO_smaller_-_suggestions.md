---
title: "Making Xubuntu ISO smaller - suggestions?"
date: 2011-10-27
forum: General Help
---

### Post by tdp2010 on 2011-10-27
Greetings all,

I'm looking for a little advice.  I've built a couple lightly customized Xubuntu distros in the past, taking off programs I don't use or like to make room for others that I feel are more useful.  It's just handy to be able to install the whole setup at once instead of having to install the programs individually afterward.  However, I'd like to improve on my last efforts some more with a few more programs, and now I'm facing a problem: adding the extra software pushes the size of the ISO image over 700 MB.  I want to keep the build small enough to still fit on a normal CD.  So, I'm trying to figure out which additional packages I can remove from the basic Xubuntu install without really detracting from the system's normal functioning.  Any suggestions?  I normally take out XChat, Thunderbird, all the games, and the built-in standard media players to begin with.  What other packages might not be missed very much?  Anything that takes up a lot of space in the ISO but doesn't get used very much once installed?

The distro I'll be working from is Xubuntu 10.04.  I'd like to make both 32 and 64 bit versions of the system for flexibility.  The way I usually build the system is by making a clean install of Xubuntu, removing some programs and adding others, and then using Remastersys to create a new ISO based on that system.

Thanks very much for any suggestions you guys can offer.

---

### Post by gsmanners on 2011-10-28
You might consider a lighter theme than normal (in particular, the icons might use some serious space). Fonts you don't use might use a lot of space. I hesitate to say this, but unless you use GIMP a lot (like I do) you might consider leaving that out. Honestly, any kind of package manager other than apt-get or aptitude is kind of a waste of space (lots of people use Synaptic, but it's really more of luxury than a necessity). After that, it gets really tough to choose.

---

### Post by ankspo71 on 2011-10-28
Hi,
Back when I was using remastersys I would run the application called "bleachbit" to clean out junk files and other unneeded files on the system, some of which took up alot of unnecessary space, such as localizations. I was using Gnome (Ubuntu) back then though, so I'm not sure how much junk files and other unneeded files it can remove from Xubuntu. Bleachbit itself is small in size and can be removed when your done using it.

You are probably already aware of this since you have used Remastersys before, but Remastersys has created a guide for system preparation:
[http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html)
Scroll down to see the important parts such as locating large files (which could help you determine some packages to remove) and the "distro prep" section.

That guide links to this other guide that goes into detail about packages to remove:
[http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)

Hope this helps.

---

### Post by tdp2010 on 2011-10-28
I do use GIMP a lot so it would be tough to leave that out.  Same with the fonts.  The package managers might be a good choice though since I install most things from the command line anyway.  And it is awfully redundant to have both Synaptic and Ubuntu Software Center there to do the same job.  Do you have an idea of how much space removing one or both of those might free up?

I haven't heard of Bleachbit before but it's definitely worth giving a shot.  Thanks for that suggestion and those lists of packages too, I think there's room there to find a few more less than essential programs.

---

### Post by gsmanners on 2011-10-28
Each individual package doesn't really use much space, but there are so many packages that they do add up. The trick to get an ISO really small is simply finding the hundreds of packages you can live without.

---

### Post by Jose Catre-Vandis on 2011-10-28
Best to build up your distro from a command line installation base, that way you only install what you need.

---

