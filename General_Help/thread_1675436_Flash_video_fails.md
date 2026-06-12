---
title: "Flash video fails"
date: 2011-01-25
forum: General Help
---

### Post by Rob Glenn on 2011-01-25
I have one Ubuntu 10.04 machine on which flash video no longer works correctly.  This appears to have broke due to updates about a month ago.  Some sites work but not others, for example Youtube videos play but not Metacafe.  What happens is everything loads, and then there  is just a white (or black) screen where the video is supposed to be.  If I right-click in that area, I get the usual context menu for Adobe flash player, just, no video.

On two other machine I have it works right.  All machines are upgraded to the latest updates.  It even works on a fresh install on a separate partition on the problem machine (however I only consider re-installing a last-ditch effort, because I have a huge amount of time invested in configuring the install I have.)

The Adobe website reports the correct version of Flash, and I've also tried installing the Chrome Browser.  At this point I think I've ruled out the Flash plugin itself, or the browser, as the cause of trouble.  It is some interaction with some other system component, but what?

Anybody have a clue how to debug this?

Thanks,
Rob

---

### Post by ajgreeny on 2011-01-25
I suggest you download and install the **flash-aid** add-on for firefox from lovinglinux, a forum member here, [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and let that do its stuff.

It will remove any problem or conflicting plugins and then get hold of the most recent flash plugin from adobe and install it with the best configuration for your machine and hardware.

---

### Post by ubudog on 2011-01-25
+1

I also suggest installing the restricted extras package.  It installs Flash, DVD codecs, etc.  It's pretty useful to have.

You can get it by typing the following into a terminal.

```
sudo apt-get install ubuntu-restricted-extras
```

Hope that helps you, it always does it for me.

---

### Post by Rob Glenn on 2011-01-25
Thanks for suggestions.  I tried Flash Aid and it didn't fix the problem, although it did pull the latest beta version from the Adobe site.  I put the Restricted Extras package on when I first installed  10.04.

---

### Post by ubudog on 2011-01-25
> **Rob Glenn said:**
> Thanks for suggestions.  I tried Flash Aid and it didn't fix the problem, although it did pull the latest beta version from the Adobe site.  I put the Restricted Extras package on when I first installed  10.04.

Hmm...

Maybe try downloading the flash player from Adobe directly, running the install script, then trying Firefox.  That may work.  Kinda weird that ubuntu-restricted-extras didn't help.  Are you using 32 or 64bit Ubuntu?

---

### Post by Rob Glenn on 2011-01-27
I fixed this, but it was tedious and I never completely figured out why it broke.  I installed the debug version of the Flash plugin from Adobe.  The error messages seemed to indicate that the video player object creation was failing, although it did not say why.  In the end I ended up backing up my home directory, deleting and re-creating my user account (a bit of a head banger since the user manager application doesn't seem to be completely stable when one is logged in as root), and copying back over all the relevant data and configs from the backup.

---

