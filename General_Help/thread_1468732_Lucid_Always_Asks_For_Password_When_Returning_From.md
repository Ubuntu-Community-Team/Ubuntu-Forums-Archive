---
title: "Lucid Always Asks For Password When Returning From Idle"
date: 2010-05-01
forum: General Help
---

### Post by X-Malleus on 2010-05-01
I do like a lot of the  changes they've made in Lucid (especially the aesthetic ones), but there is one change they made that I don't like, and I can't figure out how to get around it.  I have Ubuntu set so that, after 10 minutes or so of inactivity, my screen is blanked, in order to save power.  In Lucid, though, whenever I come back to my computer after the screen has been blanked, it requires me to entire my password in order to resume use of my computer.  Is there any way I can turn this off?

This next question is unrelated, but I do still feel the need to ask.  Why, exactly, did they move the minimize/maximize/close buttons from the top-right corner of the window to the top-left?  I know that  it probably feels natural to Mac users, but every previous version of Ubuntu has had these buttons in the top-right corner.....why on earth did they feel the need to change it?  I've been using Ubuntu for a while now, and it's kind of annoying.  Surely most people who've been using Ubuntu for a while were thrown off by this, as well?  I doubt that there is any way to change it, but does anyone know if there is?

---

### Post by wojox on 2010-05-01
#1 Go to System > Preferences > Screensaver and uncheck Lock screen when screensaver is active.

#2 [http://wojox.homelinux.org/?p=65](http://wojox.homelinux.org/?p=65)

---

### Post by 73ckn797 on 2010-05-01
If the screen saver is set to blank the screen you can disable the password requirement from System/Preferences/Screensaver. Click off "Lock screen when screensaver is idle".

Follow this link to reposition the buttons to the right side as before:
[http://ubuntuforums.org/showthread.php?t=1340409](http://ubuntuforums.org/showthread.php?t=1340409)

---

### Post by coffeecat on 2010-05-01
If you really want the buttons on the right, it's not a good idea to use gconf-editor - despite the fact that half the world is telling you to do so. Have a look at this thread, which also tells you how to use the Appearance settings utility.

[http://ubuntuforums.org/showthread.php?t=1463878](http://ubuntuforums.org/showthread.php?t=1463878)

---

### Post by X-Malleus on 2010-05-01
Thanks for all the responses!  My problems have been solved : )

---

### Post by eaidoido on 2010-05-11
ubuntu menu: system/pref/screensaver preferences

[unchecked] Activate screensaver when computer is idle
[unchecked] Lock screen when screensaver is active


gconf-editor: /apps/gnome-power-management/lock

everything unchecked *except* gnome_keyring_hibernate

but i *still* am prompted for a password upon resuming from the suspend state. what am i missing?

---

### Post by eaidoido on 2010-05-16
i can confirm the following resolves this issue with lucid using gnome 2.30

"...

This seems to resolve the problem - after doing the steps above - 

open terminal "gconf-editor". 
I went to "Desktop-->Gnome-->Lockdown" then checked the box for "disable_lock_screen"

All good now"

-itslofty

full thread: [http://ubuntuforums.org/showthread.php?t=1466504&page=2](http://ubuntuforums.org/showthread.php?t=1466504&page=2)

---

### Post by cmcanulty on 2010-05-20
Well 2 of our library computers are clearly set to disable lock screen and they lock anyway even in the midst of working suddenly it goes on lockdown. I need a fix soon.

---

### Post by eaidoido on 2010-05-20
i assume youve done everything in this thread. possibly a larger issue than whats discussed in this thread?

---

### Post by cmcanulty on 2010-05-21
Yes I have everything set to no login and no lock screen and no screensaver. Doing it every few minutes now on 2 public computers, started since Lucid, very buggy distro!

---

### Post by nugencs on 2010-06-06
launch gconf-editor (alt-f2 --> type gconf-editor --> click run).

go to apps->gnome-power-manager->lock->check use_screensaver_settings

---

### Post by cmcanulty on 2010-06-07
As I said I already set screensaver to never

---

### Post by nugencs on 2010-06-07
of course. but as long as the above option's not checked, the gnome power manager will just override your screensaver's settings. it (power manager) will still suspend your screen no matter how you disable it (screensaver). anyway, this worked for me...

---

### Post by cmcanulty on 2010-06-07
OK thanks now I understand. I thought the pref screensaver setting to uncheck did that same thing but I guess not.

---

