---
title: "Updating my game (Wesnoth)"
date: 2010-04-13
forum: General Help
---

### Post by kakarotman on 2010-04-13
So i am running Kubuntu with kde4 on my laptop. The game Wesnoth recently got updated to 1.8 and when i go to kpackagekit it does not show wesnoth 1.8 it only shows 1.6.5 or whatever. This may have something to do with my repository (<----- Know very little about), and i just really need to get this new version so any help would be greatly appriciated.

---

### Post by kakarotman on 2010-04-13
bump

---

### Post by Untitled_No4 on 2010-04-13
From [http://wiki.wesnoth.org/WesnothBinariesLinux#Karmic:](http://wiki.wesnoth.org/WesnothBinariesLinux#Karmic:)
> 9.10's universe repository includes version 1.6.5.

You can install via Applications->Ubuntu Software Center, via System->Administration->Synaptic, or aptitude/apt-get.

Also, IT-WESNOTH offers additional builds of the stable and development releases in their repository on tuxfamily: [1]. Please report issues with these packages to them and not to Ubuntu/the wesnoth team!

It is not very likely that an Ubuntu repository for a non-development release (such as Karmic) will include version updates to a package.

It seems that the version included in Lucid is also 1.6.5 and it will probably won't be updated to 1.8 before 1.8 is stable. 

So, in other words, you will have to find another source for it. The page above mentions IT-WESNOTH as a source for development releases so I think your best bet is visiting their website (link is on the page) to see if they have a deb file of the development release.

---

