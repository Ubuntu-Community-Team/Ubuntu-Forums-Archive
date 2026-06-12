---
title: "What's with different repositories for different releases?"
date: 2010-12-16
forum: General Help
---

### Post by Scooter_X on 2010-12-16
So yea, why are there so many repositories for the same source (playdeb for example) that specify lucid from maverick or karmic? Why doesn't the repository work on Lucid if it's a repository for Maverick? A big question is why I can't get access to playdeb's stuff on a Lubuntu installation. Any help including links is appreciated. Thanks gang.

---

### Post by timgood on 2010-12-16
This is because the .deb files available in the repositories have been tested and proved to work on a particular version of Ubuntu. Changes in the OS will sometimes make applications no longer work, so new versions need to be released. Sometimes these are not compatible with older OS builds.

I can only assume that playdeb files are not tested for compatibility on LUbuntu systems.

Hope this helps.

---

### Post by QLee on 2010-12-16
And Scooter_X, specifically about playdeb, it's third party software, not a part of Ubuntu. You can't expect Ubuntu maintainers to include it in the official repositories.

Here's a link, found with a brief Google search, which might help you:
[http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install](http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install)

---

### Post by Scooter_X on 2010-12-16
Ok cool. That clears things up. 

Is there no way to rip a .deb out of a repository just to test and see if it works?

---

### Post by QLee on 2010-12-17
[QUOTE=Scooter_X]...
Is there no way to rip a .deb out of a repository just to test and see if it works?[/QUOTE]

Sure it's possible, but you probably shouldn't unless you have considerable experience.

The package managers handle dependencies of a package for you and those dependencies can cause you big problems. 

If a package is essentially "stand alone" and doesn't depend on any packages or package versions not already on you system, then you'd not have trouble. The oldschool manual method was, and is, a pain and even though I like the command line, I don't favour or recommend what you are asking about. Someone will probably post how to do it though, just be careful what you wish for.

---

