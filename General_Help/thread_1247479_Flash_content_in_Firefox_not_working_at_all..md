---
title: "Flash content in Firefox not working at all."
date: 2009-08-23
forum: General Help
---

### Post by mbuehl on 2009-08-23
As an example:

[http://www.candystand.com/play/the-space-game](http://www.candystand.com/play/the-space-game)

just loads and flashes the game over and over. Not sure what I'm doing wrong... please help?

to clarify, I've run [COLOR=#677788][FONT=Arial][COLOR=#677788][COLOR=#677788][COLOR=#677788]sudo apt-get [/COLOR][/COLOR][/COLOR][/FONT][/COLOR][COLOR=#677788][FONT=Arial][COLOR=#677788][COLOR=#677788][COLOR=#677788]install f[/COLOR][/COLOR][/COLOR][/FONT][/COLOR][COLOR=#677788][FONT=Arial][COLOR=#677788][COLOR=#677788][COLOR=#677788]lashplugin-nonfree - which reports that the installation has already taken place, is up to date, and no changes are needed. Ive rebooted, twice for good measure. Still freaks out at me. If a flash application DOES manage to load it rarely runs well, usually very buggy/choppy/undesirably crappy in general.
[/COLOR][/COLOR][/COLOR][/FONT][/COLOR]

---

### Post by mbuehl on 2009-08-23
pretty please?

---

### Post by zieglerj on 2010-08-10
I've go the same problem but, as of yet, no solution. Attempting to load videos in Hulu gets the message "Hulu's flash player doesn't work with 64bit flash" or something of the like.

---

### Post by luigi_mb on 2010-08-11
Using Synaptic, uninstall "flashplugin-nonfree". Then select and install "adobe-flashplugin". This is the very latest version, which corrects vulnerabilities etc.


/luigi

---

### Post by savaan on 2010-08-12
I've had flash probs for months like this but can't seem to get it fixed. I've removed the nonfree plugin, but the plugin "adobe-flashplugin" simply doesn't exist in my synaptic manager

---

### Post by rawlins02 on 2010-08-12
adobe-flashplugin is located in the external repository (archive.canonical.com/partner).  Have you enabled downloads from Canonical?  Go to Synaptic and check under Settings -> Repositories.

---

### Post by savaan on 2010-08-12
yes that was checked. i'm on karmic if thats any help

---

### Post by clhsharky on 2010-08-12
savaan

Try flash-aid by lovinglinux
[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

Sharky

---

