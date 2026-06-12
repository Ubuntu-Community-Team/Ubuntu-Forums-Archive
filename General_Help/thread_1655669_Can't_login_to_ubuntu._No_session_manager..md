---
title: "Can't login to ubuntu. No session manager."
date: 2010-12-29
forum: General Help
---

### Post by u-noob-tu on 2010-12-29
The other day I installed a gnome theme that required nautilus. I didn't like the theme as much as I thought I would so I uninstalled it and nautilus since I no longer needed it. I logged out just a few minutes ago and I can't log back in. It brings me back to the login screen with no error message or anything. Strangely thaw session manager seems to be gone. It occured to me that while I was uninstalling nautilus I saw the words "gnome-session manager" in the terminal. But nautilus and gnome session have nothing to with each other. Is there any way I can get back into ubuntu or did I screw up?

---

### Post by u-noob-tu on 2010-12-30
I am the luckiest son of a gun who has ever lived. after doing some digging i discovered that uninstalling nautilus actually uninstalled almost everything needed to run gnome desktop, INCLUDING gnome desktop. so i managed to reinstall everything from the recovery console and, to my incredible relief, everything was just the way i had left it. im still wondering why getting rid of nautilus would do all that. i hadnt had nautilus before this. is it really that important?

---

### Post by mcduck on 2010-12-30
If you used Gnome, then yes, you *did* have Nautilus before.

It's Gnome's file manager, and also handles the desktop for you. Pretty much the first thing you see when you log into Gnome is Nautilus. And every time you open any location in File Manager you are using Nautilus as well... :)

---

### Post by cgroza on 2010-12-30
You can't ger rid of nautilus in gnome. It is everywhere!:lolflag:

---

### Post by u-noob-tu on 2010-12-30
well now i know :p i do have a a question though: when i installed nautilus when trying to get that theme to work, i opened up my file manager and it looked different. if it was there to begin with, why did it change? im still very new at ubuntu/linux, but im having a blast learning it. :lolflag:

---

### Post by mcduck on 2010-12-30
> **u-noob-tu said:**
> well now i know :p i do have a a question though: when i installed nautilus when trying to get that theme to work, i opened up my file manager and it looked different. if it was there to begin with, why did it change? im still very new at ubuntu/linux, but im having a blast learning it. :lolflag:

Are you sure you installed Nautilus (which should be pretty hard to install, as it's already installed), and nor *Nautilus-Elementary* (a fork of Nautilus, with different user interface and some additional features).

In that case just disable the repository where you got Nautilus-Elementary, and then install the "ubuntu-desktop" metapackage. It will install everything that's included in the default Ubuntu setup, which should give you back both Nautilus and gnome-session-manager, plus everything else that might have been removed when you uninstalled Nautilus...

---

### Post by u-noob-tu on 2010-12-30
> **mcduck said:**
> Are you sure you installed Nautilus (which should be pretty hard to install, as it's already installed), and nor *Nautilus-Elementary* (a fork of Nautilus, with different user interface and some additional features).

In that case just disable the repository where you got Nautilus-Elementary, and then install the "ubuntu-desktop" metapackage. It will install everything that's included in the default Ubuntu setup, which should give you back both Nautilus and gnome-session-manager, plus everything else that might have been removed when you uninstalled Nautilus...

theres the problem. i installed nautilus-elementary. how did i forget that? :mad: i managed to get everything back just the way it was, thank God [-o<. nothing seems to be missing, so i guess im good for now.

---

