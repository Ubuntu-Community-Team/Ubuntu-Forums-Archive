---
title: "FireFix didn't upgrade 1503 to 1504"
date: 2006-06-09
forum: General Help
---

### Post by dallas7 on 2006-06-09
Oops.  I meant FireFox in that subject line, not FireFix...

I did today's "automatic upgrade" via the Update Manager which included, among some others, FireFox 1.5.0.4.

However, my FireFox Help > About still shows it as 1.5.0.3.
AND... my Help > Check for Updates is greyed out - I can't even use the resident upgrade tool!

What went wrong?

Thank you.

---

### Post by Mirrorball on 2006-06-09
Stupid question: Did you restart it?

---

### Post by dallas7 on 2006-06-10
I should have mentioned: I closed FireFox, did the upgrade, and opened FireFox.  I restarted it several times after that just to make sure.  I actually close all running apps before any upgrades.

I'm not so much concerned the upgrade might not have taken as I am that the FireFox's resident upgrade tool is now broken.

Thanks for your response.

---

### Post by Ramses de Norre on 2006-06-10
Are you running a 1.5.0.3 version you installed in breezy next to the ubuntu version? If so follow the steps to remove that version from [here]("https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c") and use the ubuntu version again (which should've been upgraded).

---

### Post by JA2 on 2006-06-10
The FF update worked for me...

---

### Post by fbonjour on 2006-06-10
Hi,

I had problems with teh upgrade too. I didn't realize FF was running when I launched the upgrade, but after the upgrade was complete, I restarted it and it hasn't worked properly since:

* The main problem seems to be chrome. When I try for instance to edit my preferences, I get a pop up with the following message:

"XML Parsing Error: syntax error
Location: chrome://browser/content/preferences/preferences.xul
Line Number 1, Column 1:ssed = true;
^"

(less the quote marks, of course). I get somilar messages if I try to do other things like edit my bookmarks or call the help contents.

* Some weblages don't work, for instance Wikipedia. If I go to any wikipedia page, I get all the page's main contents, then, below it at the end I get the left-hand frame with the menus and the search form.

* I also noted something else strange things, but I guess it's unrelated: for instance, if I delete my "${HOME}/.mozilla/firefox" dir and restart FF, I still get my old bookmarks.

* If I select the "About Mozilla Firefox" menu item, no new window appears at all.

* Here are the packages installed this morning:

"Commit Log for Sat Jun 10 08:38:41 2006

Upgraded the following packages:
binutils (2.16.1cvs20060117-1ubuntu2) to 2.16.1cvs20060117-1ubuntu2.1
binutils-static (2.16.1cvs20060117-1ubuntu2) to 2.16.1cvs20060117-1ubuntu2.1
firefox (1.5.dfsg+1.5.0.3-0ubuntu3) to 1.5.dfsg+1.5.0.4-0ubuntu6.06
firefox-dom-inspector (1.5.dfsg+1.5.0.3-0ubuntu3) to 1.5.dfsg+1.5.0.4-0ubuntu6.06
firefox-gnome-support (1.5.dfsg+1.5.0.3-0ubuntu3) to 1.5.dfsg+1.5.0.4-0ubuntu6.06
gdm (2.14.6-0ubuntu2) to 2.14.6-0ubuntu2.1
libnspr4 (2:1.firefox1.5.dfsg+1.5.0.3-0ubuntu3) to 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06
libnss3 (2:1.firefox1.5.dfsg+1.5.0.3-0ubuntu3) to 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06
libpq4 (8.1.3-4) to 8.1.4-0ubuntu1"

So far I have reinstalled all packages with firefox in the name, and that did nothing.

I also tried starting FF from the command line, even with strace to see if I got more information, but didn't get very far.

Any suggestions would be appreciated!

Filipe

---

### Post by fbonjour on 2006-06-10
[QUOTE=JA2]The FF update worked for me...[/QUOTE]

Your profile says you're using 5.10, which I thought didn't have FF 1.5...

Filipe

---

### Post by fbonjour on 2006-06-10
[QUOTE=fbonjour]Hi,

I had problems with the upgrade too.[/QUOTE]

It's working now, don't know why. My best guess is that some process launched during the upgrade took 12 hours to complete, strange as it seems... It all looks OK now: I'm running version 1.0.5.4, Wikipedia looks normal, when I start FF it tries again to read the profile from .mozilla/firefox, the help, about and preferences menu items work...

Strange. Apologies for the needless post.

Filipe

---

### Post by dallas7 on 2006-06-11
[QUOTE=Ramses de Norre]Are you running a 1.5.0.3 version you installed in breezy next to the ubuntu version? If so follow the steps to remove that version from [here]("https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c") and use the ubuntu version again (which should've been upgraded).[/QUOTE]

Yes.  And on top of that, the upgrade to 6.06.  What a mess!
Anyhow, I followed those steps and that broke FF altogether.
Then I really managed to muck things up by playing with add/remove and Synaptics.

So, I bit the bullet and wiped the hard drive and started from scratch with a clean 6.06 install.  From now on I'm going to keep things simple and not stray from the Ubuntu Way.

Thanks for your input!

---

### Post by dallas7 on 2006-06-11
[QUOTE=JA2]The FF update worked for me...[/QUOTE]

Well, good for you.

---

