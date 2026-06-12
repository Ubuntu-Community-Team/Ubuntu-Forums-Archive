---
title: "How to update a program using terminal?"
date: 2011-01-16
forum: General Help
---

### Post by listerdl on 2011-01-16
Hi sorry i should know this but just to be sure, to update bluefish the html editor, do I do:

sudo apt-get update bluefish

just want to get it right before i try thanks a lot.

---

### Post by veggen on 2011-01-16
Manuals are your friends.
In your command, substitute 'update' with 'upgrade', or just try an install again. If there's a newer version, it should inform you and ask to upgrade.

---

### Post by corncob on 2011-01-16
> **listerdl said:**
> Hi sorry i should know this but just to be sure, to update bluefish the html editor, do I do:

sudo apt-get update bluefish

just want to get it right before i try thanks a lot.

I think that update will just update your sources list, the same thing as clicking RELOAD in Synaptic Package Manager.  After that you can mark Bluefish for upgrade and Apply.

---

### Post by e_torano on 2011-01-16
> **veggen said:**
> Manuals are your friends.
In your command, substitute 'update' with 'upgrade', or just try an install again. If there's a newer version, it should inform you and ask to upgrade.

This is what Id do. I'd run sudo apt-get update first to update the sources list, then I'd run upgrade to do the actual upgrade.

---

### Post by Frogs Hair on 2011-01-16
If your not able to get the latest version though the terminal , here is a link.[http://bluefish.openoffice.nl/download.html](http://bluefish.openoffice.nl/download.html)

---

