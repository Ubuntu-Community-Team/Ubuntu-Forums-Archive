---
title: "Notification and Indicator icon woes"
date: 2011-11-21
forum: General Help
---

### Post by Calcipher on 2011-11-21
I am running Xubuntu 11.10x64 and I'm having a few problems related to the various indication/notification icons.  First off, if I go to "Panel Preferences"->"Items" and click on "Notification Area"'s properties I see that there is an entry for "Xfce Power Manager" (working as expected) and "Power Manager".  The latter has a constant icon that, when hovered over, tells me that my battery is charged.  I cannot seem to get rid of this icon and clicking on it does absolutely nothing.  I made sure gnome-power-manager was not installed (it wasn't) and then decided to install it just to see if it'd add some sort of back end to the icon that was missing and I could remove it; still no way to interact with the icon or remove it.

Second, my volume icon has vanished.  Now, I do not use Xfce's mixer because it isn't compatible with Pulse and I have pavucontrol and gnome-media installed.  At first, I had two volume icons (xfce's mixer and gnome-media's); I removed xfce's stuff and that left me with just gnome-media's.  Now, however, gnome-media's icon is gone and I can't find a way to get it back.

Finally, dropbox's icon has completely vacated.  I installed Dropbox via instructions I found for non-nautilus environments.  This worked great and gave me the standard dropbox notification icon, but this too vanished.  I know dropbox is working and syncing, but no icon.

If anyone could help me I'd very much appreciate it.  I care less about the Dropbox issue than the others, but would appreciate help there if anyone has had the same issue.
Thanks.

---

### Post by LewisTM on 2011-11-22
1) Power Manager
Not sure what that icon does, but why don't you just set it as hidden in the notification area preferences?
2) Sound
Make sure the indicator plugin is in your panel and that indicator-sound-gtk2 package is installed. This indicator will interact with Pulse. You could also experiment with removing Pulseaudio altogether. If it works (you would be left with ALSA) then things like the xfce mixer and volume/mute keys would function properly.
3) Dropbox - I leave that to others

Cheers!

---

### Post by Calcipher on 2011-11-22
Thanks for the help.  Despite rebooting several times yesterday with no result, the power icon just vanished this morning.  No idea what that was all about, but farewell.  As far as the sound icon, I had indicator-sound, but not indicator-sound-gtk2 installed - I've installed it and we'll see if that fixes it on the next reboot.

Finally, there is the issue of Dropbox.  I realized yesterday that there is actually a dropbox installer in the repos called 'nautilus-dropbox'.  I removed all of the stuff I'd done to get it working before, installed nautilus-dropbox, and found that thins work even without nautilus.

---

