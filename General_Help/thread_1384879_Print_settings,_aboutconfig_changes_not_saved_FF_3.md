---
title: "Print settings, about:config changes not saved FF 3.5x"
date: 2010-01-18
forum: General Help
---

### Post by BreeHam on 2010-01-18
Hi All,

I am using Firefox in Ubunt 9.10.  When I used FF v. 3.016 under Ubuntu 9.04, I had no problems with printing or setting about:config preferences. Now I have updated to Ubuntu 9.10 and Firefox 3.5.3 through 3.5.7, I find my print settings do not hold (they revert to the Draft setting provided by my printer driver). Worse, when I go into about:config, _those_ settings do not hold, either.  The next time I restart Firefox or go into about:config, they have reset to their previous values.

The net result is that Firefox defaults to using my print driver at a draft setting unless I reset it each and every time I wish to print. Printing continues to work normally in every other application. I have isolated the problem to Firefox 3.5x in Ubuntu, as printing in both Ubuntu versions 9.04 and 9.10 works fine.  Firefox 3.0x worked fine in an earlier Wubi install of 9.10.  The problem comes with the upgrade from Firefox 3.x to 3.5x. Unfortunately, FF v.3.5x comes installed with Ubuntu 9.10.   The same problem continues whether I am running from a Live disk or a full installation to a dedicated partition.

This is a "base" install of Firefox and there are no additional add-ons or customizations to cause conflicts. Removing the version of Firefox supplied by the Ubuntu 9.10 repository and replacing it with a download from Mozilla makes no difference. 

I have tried everything suggested in the Ubuntu and Firefox support and help files and forums, including deleting the prefs.js file on the chance it is corrupted and resetting all print options to default in about:config (which are also not saved). There are no user.js files or numbered .js files present that I can find, so I don't believe preferences in those are pre-empting those in about:config. For me, Firefox 3.5 in Ubuntu now behaves as if the user settings are locked, and in fact, changes to the settings made in about:config also do not hold. Oddly, bookmarks can be saved and Firefox accepts new add-ons and customizations.

I so hope someone can help, as this has rendered my Ubuntu/Firefox partition nearly useless for websurfing, as all printing defaults to draft. I have had to return to using my Windows 7/XP partitions in my tri-boot system, where Firefox 3.5.7 works fine.

Thanks so much to anyone who can help; I want my Ubuntu back; I miss it! -- Bree.

---

