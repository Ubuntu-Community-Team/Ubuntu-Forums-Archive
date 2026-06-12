---
title: "General question regarding packages"
date: 2005-01-26
forum: General Help
---

### Post by andrewski on 2005-01-26
I'm new to Ubuntu, from Gentoo, and I'm really impressed so far.  Good work devs!

I've switched to Hoary and enabled the main/restricted/universe/multiverse sections and as I've been searching in the Synaptic, there are certain packages that I've been looking for that I haven't found, most notably Xfce 4.2.0.  Is there a way I can create packages that can be submitted for possible future inclusion in the future?  For example, I know there are third-party Xfce packages, but I'd prefer just to use Ubuntu packages specifically.

The thing I really liked about Gentoo was not the compiling from source to be ultra-733T but rather the vast number of programs they had in their central repository.  I'd be interested in helping Ubuntu's repository grow as well. :-D 

Thanks a lot.

---

### Post by fng on 2005-01-26
the warty repositories are a copy from debian unstable around april 2004.  New version of packages that were released after that date, will most like not be in warty.  But there are exceptions.

When warty was released, all developpers moved on to hoary.  Only security updates are released for warty (till 18 months after the release date).  A new copy from debian unstable was made -> hoary repo. 

xfce4.2 wont be released for warty by the official developpers.  It will be in hoary.

---

### Post by andrewski on 2005-01-26
Well, as I pointed out in my initial post, I already upgraded to hoary.  Quick and easy process, thanks to synaptic.

So, question is, how can I help get Xfce 4.2.0 into hoary's universe?  And how do I make packages in general?  Is there a good how-to?

---

### Post by fng on 2005-01-27
Packages in general :
There ia a debian guide : [http://www.debian.org/doc/maint-guide](http://www.debian.org/doc/maint-guide)  
But i find it rather difficult to understand with absolutely no help.  

I have lots lying around (Openttd, Crafty, Oki, Fifteen, Blobwars, Wesnoth, new fortune files, ...) , just waiting to be packaged and put on a repo.  They all work fine on my local installation.

Getting Packages into the hoary universe wont be easy unless you are a real develloper.  Its best to host your own repository and put the packages there.  Then just spread the url in the forums and people will have no problem using your packages.

---

### Post by andrewski on 2005-01-27
[QUOTE=fng]Getting Packages into the hoary universe wont be easy unless you are a real develloper.  Its best to host your own repository and put the packages there.  Then just spread the url in the forums and people will have no problem using your packages.[/QUOTE]Well, that is entirely frustrating.  If I do that, soon I will have a sources.list file a miles long, some with packages that conflict (in case of dups) and to find them, I have to scour the forums looking for URLs.

I'm *really* not trying to troll, but to understand why this is set up this way; why isn't the universe repository open to user input?  Or put another way, why aren't there more (less involved) developers?

---

### Post by JoWilly on 2005-01-29
Have you been here ? : [http://www.ubuntulinux.org/wiki/DeveloperResources](http://www.ubuntulinux.org/wiki/DeveloperResources)

---

### Post by andrewski on 2005-01-30
[QUOTE=JoWilly]Have you been here ? : [http://www.ubuntulinux.org/wiki/DeveloperResources](http://www.ubuntulinux.org/wiki/DeveloperResources)[/QUOTE]/me adds to my bookmarks.  Thanks for that!

---

