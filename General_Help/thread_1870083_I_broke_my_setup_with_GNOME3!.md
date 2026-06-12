---
title: "I broke my setup with GNOME3!"
date: 2011-10-26
forum: General Help
---

### Post by linuxuser12345 on 2011-10-26
I have been messing around with GNOME 3 and now my system settings have been totally screwed up when I try to go back and use Unity! My maximize button is gone and the the aero-snap-like feature doesn't work when I try to use Unity. When I use GNOME 3 with the Gnome-tweak utility installed, I have to log out and log back in for changes to the theme to take place, and amost of the time the GTK theme doesn't match the window border theme! Can someone help me?

Is there a way I can fix this and make it so when I change a setting using one GUI it doesn't screw up the next GUI?

I am using Ubuntu 11.10 x64.

---

### Post by oldtimer7777 on 2011-10-26
I personally installed Gnome 3 on Ubuntu 11.10 and things stopped working after the last batch of updates from the Gnome developers PPA.   Hopefully if you installed Gnome 3 from the PPA, you can just do a PPA purge like this to clean it out:

```
sudo apt-get install ppa-purge 
sudo ppa-purge ppa:gnome3-team/gnome3 
sudo ppa-purge ppa:ricotz/testing 
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install ubuntu-desktop
```

One of the features that stopped working after those latest updates from the developers was the ability to access the User Accounts to change settings from the GUI. I did the purge and my system works the way it did before I installed Gnome 3. 

> **linuxuser12345 said:**
> I have been messing around with GNOME 3 and now my system settings have been totally screwed up when I try to go back and use Unity! My maximize button is gone and the the aero-snap-like feature doesn't work when I try to use Unity. When I use GNOME 3 with the Gnome-tweak utility installed, I have to log out and log back in for changes to the theme to take place, and amost of the time the GTK theme doesn't match the window border theme! Can someone help me?

I am using Ubuntu 11.10 x64.

---

### Post by linuxuser12345 on 2011-10-26
I didn't use the PPA! :(

---

### Post by oldtimer7777 on 2011-10-26
> **linuxuser12345 said:**
> I didn't use the PPA! :(

Then uninstall it from the synaptic package manager? 

```

sudo apt-get install synaptic
sudo synaptic

```

Remove the package you used to install Gnome 3.

---

### Post by MG&amp;TL on 2011-10-26
> **linuxuser12345 said:**
>  When I use GNOME 3 with the Gnome-tweak utility installed, I have to log out and log back in for changes to the theme to take place, and amost of the time the GTK theme doesn't match the window border theme! Can someone help me?

I am using Ubuntu 11.10 x64.

Can't help with first bit, but the bit about logging in and out, that's normal. You can get around that by reloading gnome-shell (Alt-F2, "r").

No, the icon set and the window theme are separate entities.

---

### Post by linuxuser12345 on 2011-10-26
I ended up formatting and reinstalling. Everything is fine now, though! Thanks for all your help :)

---

