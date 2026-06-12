---
title: "Firefox won't load"
date: 2010-01-16
forum: General Help
---

### Post by rbateai on 2010-01-16
Hi!
I installed 9.10 on a dual boot XP machine. It seemed to install fine and update manager brought it all up to date. Except, now Firefox won't load ... uninstalled and reinstalled it ... still no.
 Suggestions please.
Thanks

---

### Post by New5teve on 2010-01-16
Try opening up a console, then type in 'firefox'. That will try to load firefox, and give you a ton more information about what your computer is doing when it tries to run it. Then bring us back some info :)

---

### Post by lovinglinux on 2010-01-17
First make sure there is no firefox running without the interface, by launching the System Monitor. Kill it if necessary. Then run this on a terminal:

```
firefox -safe-mode
```

If it starts, then you have an extension messing with something. I have seen some reports of Cooliris preventing Firefox from starting.

If that doesn't help, then run this:

```
firefox -P
```

This should bring the profile manager. Create a new profile and launch it. If Firefox starts, then you have a corrupted profile. Keep the new one and delete the old one. You might want to get a bookmark backup before deleting it.

If that doesn't help then try to re-install xulrunner-1.9.x from Synaptic.

---

### Post by pjb1955 on 2010-01-17
I am having a similar problem.  I was using firefox and then it froze up on me and now it won't load.  I am a beginner here so your instructions are vague for me.  Where is the console/terminal to type the code?

---

### Post by pjb1955 on 2010-01-17
I found the terminal and did what the two of you wrote.  I get this, "Could not find compatible GRE between version 1.9.1 and 1.9.1.*

Now what?

---

### Post by lovinglinux on 2010-01-17
> **pjb1955 said:**
> I found the terminal and did what the two of you wrote.  I get this, "Could not find compatible GRE between version 1.9.1 and 1.9.1.*

Now what?

Go to Synaptic Package Manager, search for xulrunner-1.9.1, mark it for re-installation and apply. That should fix the problem.

---

### Post by rbateai on 2010-01-17
> **New5teve said:**
> Try opening up a console, then type in 'firefox'. That will try to load firefox, and give you a ton more information about what your computer is doing when it tries to run it. Then bring us back some info :)
I got  GLib WARNING **:g_set_prgname () called multiple times. ???

---

### Post by linsnd on 2010-01-18
I;m getting a similar error (firefox-bin:####) GLib-WARNING **: g_set_prgname() called multiple times?
 Any help will be a great help! thx in advance!

---

### Post by linsnd on 2010-01-18
Oka I found my problem I had a I guess "corrupted" plug-in that was causing the problem I identified the bad plugin by starting FF in safemode. in Terminal enter firefox -safe-mode then select disable all add-ons then selecting the "Make Changes and Restart button. Then I just enabled my add-ons until I found the one that caused firefox to not load and reinstalled it now all is working fine. Thanks!

---

### Post by lovinglinux on 2010-01-18
> **linsnd said:**
> Oka I found my problem I had a I guess "corrupted" plug-in that was causing the problem I identified the bad plugin by starting FF in safemode. in Terminal enter firefox -safe-mode then select disable all add-ons then selecting the "Make Changes and Restart button. Then I just enabled my add-ons until I found the one that caused firefox to not load and reinstalled it now all is working fine. Thanks!

You are welcome. It was a plugin or an extension? Would you mind sharing which extension/plugin was causing the problem? I also would recommend reporting the problem on the extension page at Mozilla Add-ons site.

---

