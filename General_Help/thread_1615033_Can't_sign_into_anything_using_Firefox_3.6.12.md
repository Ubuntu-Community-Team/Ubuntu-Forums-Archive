---
title: "Can't sign into anything using Firefox 3.6.12"
date: 2010-11-06
forum: General Help
---

### Post by Steve Francis on 2010-11-06
After a recent Ubuntu update, I can no longer sign into any accounts using Firefox.

Can't log on to Amazon, Google, Ubuntu forums...anything :mad:

I'm using Epiphany 2.28.0 at the moment to post this message.

When I enter my user name and password for any account in Firefox, it just returns the same sign-in screen with blank input boxes; or nothing happens.

I tried clearing cookies. I've tried starting FF in safe mode. Still no success.

Any ideas of what to try next, please?

---

### Post by sohlinux on 2010-11-06
sudo apt-get remove firefox

sudo apt-get install firefox

you may want to make a backup of your bookmarks before

---

### Post by Steve Francis on 2010-11-06
> **sohlinux said:**
> sudo apt-get remove firefox

sudo apt-get install firefox

you may want to make a backup of your bookmarks before

Tried this. No change, unfortunately, but thanks.

Could it be a profile setting that's causing the problem?

------------------

Just for information, when I type 'firefox' in terminal it returns:
(firefox-bin:4152): GLib-WARNING **: g_set_prgname() called multiple times

Probably unrelated.

---

### Post by sohlinux on 2010-11-06
> **Steve Francis said:**
> Tried this. No change, unfortunately, but thanks.

Could it be a profile setting that's causing the problem?

------------------

Just for information, when I type 'firefox' in terminal it returns:
(firefox-bin:4152): GLib-WARNING **: g_set_prgname() called multiple times

Probably unrelated.

you could try to remove firefox again but make sure you delete all references to it then run sudo apt-get upgrade then re install it, this has certainly fixed program issues for me in the past.

---

### Post by lovinglinux on 2010-11-06
> **sohlinux said:**
> sudo apt-get remove firefox

sudo apt-get install firefox

you may want to make a backup of your bookmarks before

Reinstalling Firefox does not delete your Bookmarks or any personal settings, which are stored in your personal profile folder under the ~/.mozilla/firefox

> **sohlinux said:**
> you could try to remove firefox again but make sure you delete all references to it then run sudo apt-get upgrade then re install it, this has certainly fixed other program issues for me in the past.

It won't help.

> **Steve Francis said:**
> 

Could it be a profile setting that's causing the problem?


Probably. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial and [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

---

### Post by sohlinux on 2010-11-06
> **lovinglinux said:**
> Reinstalling Firefox does not delete your Bookmarks or any personal settings, which are stored in your personal profile folder under the ~/.mozilla/firefox



It won't help.




Probably. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial and [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

[COLOR="Red"]I said backup just as a precaution 

remove all references to firefox because some personal file may be corrupt - then update and upgrade apt-get to be sure to get the latest package then re install, it worked for me[/COLOR]

---

### Post by Steve Francis on 2010-11-06
> **lovinglinux said:**
> See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial and [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

Deleted the folder ~/.mozilla/firefox and restarted Firefox*.

Problem solved. Thanks :)

(*Note to anyone trying this - your Firefox settings, passwords, bookmarks, extensions, themes, cookies and other configuration files will be completely deleted. This wasn't an issue for me but it may be for you. Make the appropriate back-ups.)

---

### Post by lovinglinux on 2010-11-06
> **sohlinux said:**
> [COLOR="Red"]I said backup just as a precaution 

remove all references to firefox because some personal file may be corrupt - then update and upgrade apt-get to be sure to get the latest package then re install, it worked for me[/COLOR]

I said reinstalling won't help. Your problem was solved most likely because you deleted your profile, which I don't recommend unless there is no solution, because you will lose bookmarks, passwords and all other personal Firefox data and configuration. It usually works tho. My tutorial explains how to avoid complete deletion and how to restore important stuff if you need to do it.

---

### Post by sohlinux on 2010-11-06
> **Steve Francis said:**
> Deleted the folder ~/.mozilla/firefox and restarted Firefox*.

Problem solved. Thanks :)

(*Note to anyone trying this - your Firefox settings, passwords, bookmarks, extensions, themes, cookies and other configuration files will be completely deleted. This wasn't an issue for me but it may be for you. Make the appropriate back-ups.)

nice work :)

---

