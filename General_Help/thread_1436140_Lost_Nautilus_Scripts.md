---
title: "Lost Nautilus Scripts"
date: 2010-03-22
forum: General Help
---

### Post by Enigmapond on 2010-03-22
I've been using, for quite sometime, the nautilus script manager and the script collection just to make things a bit easier. I was doing a lot of copying, moving, etc and it was easier than the terminal. Now, I booted up this morning and they are all gone and so is the prompt in nautilus for "scripts". I purged both and re-installed and as per the script manager, (nautilus-script-manager list-available), I only have one available for audio conversion and this wasn't part of the collection but a separate install. How can I get these back?

Thank You...

---

### Post by Enigmapond on 2010-03-22
:confused:

---

### Post by AndyDeGroo on 2010-03-23
Did You look inside ~/.gnome2/nautilus-scripts/ ?
All your local scripts should be there.

If scripts are there, make sure they have executable bit set in permission. If in doubt, check Permissions tab in file properties window. The **Allow executing file as program** checkbox must be checked for nautilus to consider that file a script.

All shared scripts are stored in /usr/share/nautilus-scripts/
and that's where nautilus-script-manager looks for available scripts.

If local scripts are gone, check if any recent gnome or nautilus upgrades have messed with files in your profile drectory. But that should not be happening at all.

---

### Post by Enigmapond on 2010-03-23
Thank You for responding. Right...yes and for some reason ~/.gnome2/nautilus-scripts/ was empty!?? Also in /usr/share/nautilus-scripts/ the only thing in there is the audio conversion script which was a separate install and not part of the "collection". I have attempted to re-install the collection of scripts via "nautilus-script-collection-svn" package but they are just not there...I can't understand it. They've been there since I installed Jaunty almost a year ago.

---

### Post by Enigmapond on 2010-03-23
Ok...I downloaded the script package itself and extracted it. These are NOT the scripts I'm missing...these install properly. The scripts I am missing are the ones I used to "copy to..., Move to..., link to desktop, move to home folder, etc. Does anyone know how I can replace these? They were showing when I right-clicked and selected "scripts"....sorry for the previous misinformation...

---

### Post by wojox on 2010-03-23
Check out [G-Script]("http://g-scripts.sourceforge.net/")

---

### Post by Enigmapond on 2010-03-23
> **wojox said:**
> Check out [G-Script]("http://g-scripts.sourceforge.net/")

THank you for that. Although there were none there that I needed to replace, there were some VERY useful ones there that work very well! :D

---

### Post by Enigmapond on 2010-03-24
Thank you both for responding. I just created my own with the help of this thread. I have all the scripts back now and then some.

[http://ubuntuforums.org/showthread.php?t=101859](http://ubuntuforums.org/showthread.php?t=101859)

Cheers!

---

