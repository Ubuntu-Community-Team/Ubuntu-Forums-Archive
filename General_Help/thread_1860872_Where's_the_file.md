---
title: "Where's the file?"
date: 2011-10-15
forum: General Help
---

### Post by sg_singh on 2011-10-15
After a few issues with the upgrade I finally got the machine to boot properly again, only to find that Firefox is screwed.  I've saved the bookmarks to the desktop.  I hoped for a simple dump & re-install.  Instead, I get the following...

[FONT="Fixedsys"]"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."[/FONT]l

Nifty!  So, where is the application's profile directory to be found?  Any other ideas on how to repair this would be greatly appreciated! (All-in-all, I should have left the machine alone and ignored the upgrade...)

---

### Post by oldos2er on 2011-10-15
Firefox profiles are in ~/.mozilla/firefox

Can you run df -h and post the output here?

---

