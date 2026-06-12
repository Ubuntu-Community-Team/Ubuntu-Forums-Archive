---
title: "Big problems with Sanity Check, ICEAuthority, no /.nautilus...All I can do is log-in."
date: 2010-10-19
forum: General Help
---

### Post by kevin.bogle on 2010-10-19
I've been messing about with visual customizations using gtk and cursor modifications this morning. 

I rebooted and found that my custom login background was missing, as well as three error messages after login:
Paraphrased,
[LIST]
[*]gconf-sanity-check-2 exited with status 256

[*]Could not update ICEAuthority file file /home/meek/.ICEauthority

[*]Nautilus could not create the following required folders: /home/meek/desktop,/home/meek/.nautilus.

Before running nautilus. please create these folders or set permissions such that Nautilus can create them.

[/LIST]

I did a little digging on these here forums and found advice to change some permissions for various folders (tmp, gconf, /.nautilus, /desktop) I changed these, rebooting after each one...no dice. At this point, I still have a generic ubuntu background, can "gksu nautilus," and get to a terminal via alt+F2.

Then I followed advice to from [this ]("http://ubuntuforums.org/showthread.php?t=1587918")thread, comment # 2

REGISTRY fix:
[B]$ sudo apt-get remove gconf2 gconf2-common
[/B]**$ sudo rm -rf /etc/gconf**
$ sudo apt-get install ubuntu-desktop

Upon reboot, i receive the same errors after log-in, but this time there is no desktop background, no "gksu nautilus," and alt+f2 does nothing. I can ctrl+alt+F1, however, but haven't tried any other fixes.

TIA

Edit: Please let me know if I've posted this in the wrong sub-forum

---

### Post by kevin.bogle on 2010-10-21
I should add that running in "recovery" or "netbook" mode net the same result -- nothing works except Alt+Ctrl+F2.

---

### Post by kevin.bogle on 2010-10-29
Anybody? Today I tried using the Live 10.10 CD and ran some commands attempting to restore the desktop / install. 

Since I haven't heard from the forums, I've resigned myself to doing a clean install. Now, however, The home folder won't show me my encrypted files and I have no way I know to back them up.

Le sigh

---

