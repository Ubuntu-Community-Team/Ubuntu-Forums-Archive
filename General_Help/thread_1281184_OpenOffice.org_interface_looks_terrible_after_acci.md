---
title: "OpenOffice.org interface looks terrible after accidental uninstall/reinstall"
date: 2009-10-03
forum: General Help
---

### Post by Shekibobo on 2009-10-03
So, I'm trying to get LAMP to work on my computer, and in following the instructions from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), I uninstalled everything as it said to.  Unfortunately, I didn't realize it was eliminating OpenOffice.org entirely from my computer.  So, I ran sudo apt-get install openoffice.org (with the repositories to get 3.1.1 back), and it installed everything again.  However, the interface looks like crap now (see attached image).  I tried to remove/reinstall several times, but nothing seems to be working to restore it to it's pretty interface.  Instead it looks like crappy Windows 95 interface.

Is there a way I can fix this?  It's driving me nuts.  All I wanted was LAMP, which always seems to be a total pain to setup.  Now I've got all these other problems I need to solve.  Also, whenever a menu is opened, it does a crazy zoom-in effect that none of my other menus are set up to do.  It's driving me crazy.  I'm close to just killing my computer at this point.

Does anyone have any idea how to fix this?

---

### Post by akakingess on 2009-10-03
[http://ubuntuforums.org/showthread.php?t=1156552&highlight=open+office+bad](http://ubuntuforums.org/showthread.php?t=1156552&highlight=open+office+bad)

See if this helps, found it with a quick search on this forum, in the meantime I will keep looking to see if there are other situations like this and if they found solutions.

---

### Post by Shekibobo on 2009-10-03
Perfect!  Thanks.  I used Synaptic to install openoffice.org-gtk, restarted the program, and it looks beautiful once again.  And those disgusting looking menus are back to my theme. Thank you so much.

---

### Post by akakingess on 2009-10-03
good deal, glad you are back up and running/looking good!!!

---

### Post by Shekibobo on 2009-10-03
[LEFT]Actually, it now that I'm using it again, it still looks like crap.  It doesn't seem to be using the fonts the nautilus has been assigned to use.  It's like it's running on a completely different system, and isn't integrating with my system settings.  I tried checking for other graphic utilities that might have been removed and need to be installed.  The fonts all look like crap, and the anti-aliasing is definitely not working.  The drop down menus are all wrong, and the toolbar menus aren't working quite right.  They match my theme, but the way the system interacts with them just isn't right.

I wish I had been running script when I uninstalled it all.  Is there any way I can look back at an old bash log and see the whole list of things that were removed when it got uninstalled? 
[/LEFT]

---

