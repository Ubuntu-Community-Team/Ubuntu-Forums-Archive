---
title: "All font disappears in Firefox"
date: 2011-09-01
forum: General Help
---

### Post by MorrisseyJ on 2011-09-01
Hi,

Having a largish problem here. I was trying to get WINE to run MSOffice 2003. When i couldn't get it to work i tried removing wine so that i could reinstall it. 

Upon removing it i have found that i have no fonts in firefox. 

As such i am sending this from Midori, which is working. I also have all my fonts in other programmes such as Libre Office. 

I tried reinstalling firefox from synaptic to no effect. 

Some fonts appeared to have been removed when i removed WINE as, among other things, i see the following in my 'history' on the ubuntu software centre:

> ttf-umefont (422-1) removed
ttf-symbol-replacement (1.2.2-0ubuntu6) removed
ttf-mscorefonts installer (3.3ubuntu3) removed
ttf-droid (1.00~b112+dfsg+1-0ubuntu1) removed

Seeing this i tried reinstalling WINE. So, now, the more recent 'history' contains the following entries:

> ttf-umefont (422-1) installed
ttf-symbol-replacement (1.2.2-0ubuntu6) installed
ttf-mscorefonts installer (3.3ubuntu3) installed
ttf-droid (1.00~b112+dfsg+1-0ubuntu1) installed

With all this done, firefox still isn't working.

Any ideas?

---

### Post by dino99 on 2011-09-01
sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure firefox

maybe check into synaptic that ubuntu-desktop is installed, and the repo activated via tab updating (main, universe, canonical partner, ...)

---

### Post by MorrisseyJ on 2011-09-01
Followed those instructions and still no joy. 

ubuntu-desktop is installed in synaptic and Universe repository is activated. 

Any other advice?

---

### Post by MorrisseyJ on 2011-09-01
Sorry, solved this problem. 

Seems the google search i was looking for was: "missing text in firefox", "not missing fonts in firefox".

Solution was here: [http://ubuntuforums.org/showthread.php?t=1008752](http://ubuntuforums.org/showthread.php?t=1008752)

It seems that i had also fiddled with the /usr/share/font folder, importing a whole bunch of fonts from my windows partition. When i deleted these all has returned to normal. 

Seems that i need to place these fonts in ~/.fonts instead.

Sorry about confusing things with my previous post. Thanks to all who looked at this and to dino99, especially, for posting a reply.

---

