---
title: "Firefox 3.5 startup issues with Ubuntu 9.10"
date: 2009-10-31
forum: General Help
---

### Post by murphykieran on 2009-10-31
Sorry if this has been posted already but a quick search doesn't reveal anything relevant.

I upgraded from 9.04 to 9.10 yesterday and I'm having a minor but very annoying issue with Firefox.

Every time I click on the Firefox icon to start it up, I get the checking for updates to extensions window that I've seen from time to time when starting Firefox, but I see it *every time* I start Firefox 3.5

Then, when it's done it's update checks, after a few seconds, it just cuts back to the Ubuntu desktop and I have to click the Firefox icon again to startup Firefox.  It then loads fine and I can browse the interwebs as normal.

Before the upgrade to 9.10, this never happened.  Firefox would periodically check for upgrades as is normal and reasonable to me, but I never had it take several seconds to check for upgrades to extensions *every single time it starts* and it's really annoying for it to simply dump back to the desktop after checking for updates, only for me to have to click the Firefox icon *again* to simply browse the web.

Is anyone else having a similar problem and is there an easy solution?

---

### Post by gdi2k on 2009-10-31
Sounds like one of the add-ons may not be compatible with the latest version and is causing issues.

To fix, start Firefox in safe mode and disable the add-ons. See here: 
[http://support.mozilla.com/en-US/kb/Safe+Mode](http://support.mozilla.com/en-US/kb/Safe+Mode) 

Once you've removed the culprit, close Firefox and open up normally (using the icon) and hopefully all should be well.

---

### Post by murphykieran on 2009-10-31
Interesting, I might try that.

Some further information, when I start Firefox 3.5 for the second time after it's done it's update routine, it takes me immediately to the LANGUAGES tab of the add-ons windows with 2 listed add-ons that it claims are recent add-ons - Firefox (en-GB) 3.5.2 and Xulrunner (en-GB) 1.9.1.2 with the option to disable or uninstall either or these.

---

### Post by gdi2k on 2009-11-01
Yes, I have exactly the same thing in my Firefox under Languages (also using en-GB locale), so that looks normal. I would go into the add-ons and disable all the non-critical stuff to see if you can fix your issues.

Otherwise you can just move your firefox profile to force a complete reset, but you will lose all your settings and bookmarks this way (although they can be restored from your old profile without too much trouble). 

The profile is located in ~/.mozilla (press CTRL+h to reveal hidden files). Do some googling before going this route to make sure you don't permanently delete anything!

---

### Post by murphykieran on 2009-11-02
I disabled and uninstalled all of my unused themes and add-ons and the problem seems to have gone away, so it looks like there was some installed extension that was causing the problem.

Thanks for the help.

---

