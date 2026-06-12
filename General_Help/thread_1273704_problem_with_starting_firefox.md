---
title: "problem with starting firefox"
date: 2009-09-23
forum: General Help
---

### Post by SOULTE on 2009-09-23
hi. On my ubuntu jaunty 32 bit with KDE 4.3 desktop installed, when i try to run firefox 3.5 it says that another instance of it is running but it's not really true! I tried to remove and install it again but the problem still exist. (I've installed it from software channel by adding its repository.)

---

### Post by mac9416 on 2009-09-23
Have you tried rebooting?

What I would do:
```
sudo killall firefox-3.5
```

If neither of those work, I assume something deeper is going on.

Good luck
-mac

---

### Post by SOULTE on 2009-09-25
> **mac9416 said:**
> Have you tried rebooting?

What I would do:
```
sudo killall firefox-3.5
```

If neither of those work, I assume something deeper is going on.

Good luck
-mac
I have rebooted many times! Just after the system is booted i try to start but the error brings up again.

---

### Post by TrakerJon on 2009-09-25
> **SOULTE said:**
> hi. On my ubuntu jaunty 32 bit with KDE 4.3 desktop installed, when i try to run firefox 3.5 it says that another instance of it is running but it's not really true! I tried to remove and install it again but the problem still exist. (I've installed it from software channel by adding its repository.)

If Firefox windows **open off screen** or are too large to use, you may need to reset Firefox's controls and toolbars.

1. Close down Firefox completely: On the Firefox window, click the File menu then select Exit.
2. From a terminal window type: firefox -safe-mode
3. Firefox should start up with a Firefox Safe Mode dialog with options.
4. Check mark Reset toolbars and controls.
5. Click Make Changes and Restart to restart Firefox

---

### Post by mac9416 on 2009-09-25
SOULTE,

Here's an idea I found here: [http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/](http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/)

> Step 1. Find your profile. This page tells you [how to find the location of your Firefox profile]("http://kb.mozillazine.org/Profile_folder#Where_is_my_profile_folder.3F"). Under Linux (e.g. Ubuntu), it will be at ~/.mozilla/firefox/[Profile name]/ . (For you, SOULTE, it may be ~/.mozilla/firefox-3.5/[Profile name]/)

Step 2. Remove the lock files. This page tells you [what the lock files are for Firefox on Windows/Linux/Mac]("http://kb.mozillazine.org/Profile_in_use"). Under Unix/Linux, you&#8217;ll need to remove two files &#8220;lock&#8221; and &#8220;.parentlock&#8221; .

I haven&#8217;t had this happen before today, but it can happen if (for example) someone turns your computer off while Firefox is running.

Hope that works.

---

### Post by SOULTE on 2009-09-26
tnx alot dudes. finally, I managed to get it work again :guitar:

> **TrakerJon said:**
> If Firefox windows **open off screen** or are too large to use, you may need to reset Firefox's controls and toolbars.

1. Close down Firefox completely: On the Firefox window, click the File menu then select Exit.
2. From a terminal window type: firefox -safe-mode
3. Firefox should start up with a Firefox Safe Mode dialog with options.
4. Check mark Reset toolbars and controls.
5. Click Make Changes and Restart to restart Firefox

tnx buddy but when i tried to start firefox in safemode that f**#$_#( (!) error appeared again. i continued with the next idea from mac9416;
 
> **mac9416 said:**
> SOULTE,

Here's an idea I found here: [http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/](http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/)

Step 1. Find your profile. This page tells you how to find the location of your Firefox profile. Under Linux (e.g. Ubuntu), it will be at ~/.mozilla/firefox/[Profile name]/ . (For you, SOULTE, it may be ~/.mozilla/firefox-3.5/[Profile name]/)

Step 2. Remove the lock files. This page tells you what the lock files are for Firefox on Windows/Linux/Mac. Under Unix/Linux, you&#8217;ll need to remove two files &#8220;lock&#8221; and &#8220;.parentlock&#8221; .

I haven&#8217;t had this happen before today, but it can happen if (for example) someone turns your computer off while Firefox is running.

Hope that works.

This is the idea that really helped me to get it work. :) I went to that profile directory but didn't find the lock files. so I deleted all of directory contents (!) and now i have the firefox started :lolflag:

tnx again for your help.

---

### Post by Steve Francis on 2009-10-03
I have the same problem with Firefox 3.0.14

Although the Lock file closes, parentlock does not. I have to manually delete it every time I reboot.

According to this thread
[http://forums.mozillazine.org/viewtopic.php?f=38&t=1408715](http://forums.mozillazine.org/viewtopic.php?f=38&t=1408715)
it may be a problem with certain add-ons, which is why only some users experience the problem.

---

### Post by akakingess on 2009-10-03
I would see if you could just create a new profile and possibly copy the bookmarks, etc. into the new profile, then. From the terminal, type firefox -p , that should start it into the profile manager, create a new one and see if that helps, then you can try to pick and choose the data you pull over from the old profile.

---

### Post by Steve Francis on 2009-10-03
> **akakingess said:**
> I would see if you could just create a new profile and possibly copy the bookmarks, etc. into the new profile, then. From the terminal, type firefox -p , that should start it into the profile manager, create a new one and see if that helps, then you can try to pick and choose the data you pull over from the old profile.

Thanks for your suggestion. I just tried this. Unfortunately, it doesn't work for me as a solution.

I can't get rid of the Ubuntu Firefox Modifications 0.7 extension but, other than that, I have no add-ons installed and the parentlock file still won't auto-delete.

My profile information is stored on a NTFS partition, but I don't think that would be an issue.

Have to hope that the next Firefox upgrade solves the problem :(

---

### Post by Steve Francis on 2009-10-05
I just tried creating a new profile in /home/steve/.mozilla/firefox, this time **without** copying any bookmark and add-ons from the old profile.

Firefox will now work properly.

'parentlock' is still not deleted from the new profile on program exit (should it be?), but this does not affect restarting Firefox after a reboot.

So maybe the problem is something to do with Ubuntu sharing a Firefox profile with XP?

---

