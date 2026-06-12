---
title: "Slow Browsing"
date: 2010-09-27
forum: General Help
---

### Post by Crizzie on 2010-09-27
Lately, I've been noticing that my firefox is really slow with browsing. It appears like sometimes my network just cuts and everything takes a long time to load. I'm positive my network doesn't disconnection because all of my other applications are still connected and running perfectly. Just loading any page within firefox takes awhile and when loading a page with a lot of image or a video just takes forever.

Is there anything I can do to speed things up?

---

### Post by sanderd17 on 2010-09-27
Well, this will probably come from a over-full firefox profile. Try to backup the firefox folder. 

If you don't mind reconfiguring firefox (re-installing the flash plugin, the add-ons, resetting the passwords ...) you can open the file manager nautilus, press ctrl+H to show the hidden folders, search for the ".mozilla" folder and rename it as ".mozilla.backup". Logout and login and open firefox.

If it's faster, start reconfiguring your settings, if it's broken or isn't faster, open nautilus again, delete the newly created ".mozilla" directory and change the ".mozilla.backup" back to ".mozilla".

If you don't get it faster, you might try chromium.

---

