---
title: "unable to right-click on Desktop"
date: 2010-01-30
forum: General Help
---

### Post by RobolaVirus on 2010-01-30
First up, thanks in advance for any ideas you guys might have.  I've exhausted my limited knowledge and nothing I've found on the internet has been any help so far...

Yesterday I was playing around with my Menu shortcuts (Ubuntu 9.10) attempting to run Nautilus as root (yeah, yeah I know).  Over the course of the night I tried it a bunch of different ways, including running it out of terminal just to make sure I had the commands right.

Already long story shorter, now I can't right click on my desktop, and non of my user desktop shortcuts appears.  The only way I can get them back is to open terminal and just type in nautilus (no su or anything, just as user).  As soon as I do my icons come back and I can right-click the desktop to get the menu.  BUT...as soon as I close the Terminal window it all goes back to how it was before - no icons, no right-clicky clicky.

If it means anything, when I initialize nautilus from terminal I get the following:

user@user:~$ nautilus

(nautilus:2247): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2247): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2247): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2247): WARNING **: No marshaller for signature of signal 'ShareCreateError'


Any help or ideas would be appreciated!

Thanks

---

