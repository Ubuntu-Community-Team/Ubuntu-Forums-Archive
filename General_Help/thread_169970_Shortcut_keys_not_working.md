---
title: "Shortcut keys not working"
date: 2006-05-03
forum: General Help
---

### Post by [S|G] on 2006-05-03
Hello, I was using my computer as usual and I noticed that pressing ALT+F4 wouldn't close a window... I found that strange, but after looking through some menus I found that it had been replaced by CTRL+Q. Well, at least it was working in some way, but it doesn't work for firefox. 

Also, ALT+TAB is not switching between applications and CTRL+TAB is not switching desktops anymore. Anyone has any idea about what is happening? :confused:

---

### Post by chriscando on 2006-05-03
Check System > Preferences > Keyboard Shortcuts to see if they are set how you like. If they are set correctly I can't imagine why they wouldn't be working.

---

### Post by [S|G] on 2006-05-03
I managed to track down the problem (appearently) and it wasn't a keyboard shortcuts problem... I tried to restart X and KDE wouldn't even start properly afterwards, it would stop ad "configuring process" stage. Then I tried to login to gnome, with no success as well... Both top and bottom panels would stay blinking.

I decided to login to console and chown my home folder again to myself, and also reset read permissions on all files. After that, I restarted kdm and everything was working again.

Still, what could have caused that? I didn't reconfigure anything nor did install anything lately. :confused:

---

### Post by [S|G] on 2006-05-04
Sorry for double-post, but the same thing happened again, after I got it fixed. I don't know what may be going on, anyone has any ideas?

Symptoms: Shortcut keys (alt+tab, alt+f4, etc) stop working suddenly. No error messages. Rebooting X would result in KDE and Gnome not loading properly.
How I fix it: Login to console, chown -R my home folder back to me and then restore read permissions.
Programs I have currently running: Firefox, Skype, Mercury Messenger, VMware, kmixer, konsole

VMware Windows has network access (read-only) to specific folders inside my home folder (no access to the home folder itself).

---

