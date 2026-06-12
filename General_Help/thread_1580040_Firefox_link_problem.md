---
title: "Firefox link problem"
date: 2010-09-22
forum: General Help
---

### Post by sparky333 on 2010-09-22
I have a problem with my Firefox (3.6.10) on Ubuntu 8.10.
It started right after I installed and uninstalled SeaMonkey.

I have a webpage on my server with a bunch of links. A couple
of them do not work correctly...when I click on them, instead
of opening them, it shows a Save to Disk window instantly and
then saves html of the page into /tmp on the root directory
of my local disk.

All other links on the page work fine.  I've reinstalled Firefox, 
removed everything from cache and deleted all files the /tmp 
directory.  It keeps saving the html file there.

I wonder if SeaMonkey changed an about:config browser 
parameter on me?  Question is, which one?

Help pls...

-sparky333

---

### Post by sparky333 on 2010-09-22
Problem solved...
It wasn't SeaMonkey!
At the same time I added an .htaccess file to the directory for that
domain. It was the standard file with standard Add Types, but it
caused the problem with both html and htm.  I realized this when 
I changed the file to .php and it worked.

-sparky333

---

### Post by lovinglinux on 2010-09-22
Backup your Firefox profile, then start Firefox in safe mode and select the option to reset preferences. Alternatively, you could simply delete *prefs.js* from your profile (browser needs to be closed).

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

