---
title: "&quot;Lock Screen&quot; in Ubuntu 11.10 fails"
date: 2012-04-25
forum: General Help
---

### Post by Zian on 2012-04-25
Context:

Ubuntu 11.10 32-bit edition
Tried uninstalling gnome screen saver and installing xscreensaver and then reverted.

Problem:

When I click on "Lock Screen" under the Gear icon, nothing happens.

Expected Result:

A locked terminal.

---

### Post by techsupport on 2012-04-25
> **Zian said:**
> Context:

Ubuntu 11.10 32-bit edition
Tried uninstalling gnome screen saver and installing xscreensaver and then reverted.

Problem:

When I click on "Lock Screen" under the Gear icon, nothing happens.

Expected Result:

A locked terminal.

Yeah, I have been having issues with Screensaver in 12.04 like this.  Screensaver needs development again since moving away from gdm.

---

### Post by sikander3786 on 2012-04-25
Try:

```
sudo apt-get purge gnome-screensaver
sudo rm /usr/bin/gnome-screensaver-command
sudo apt-get install gnome-screensaver
```

You might need to re-login after executing the above commands.

If you moved away from XScreenSaver just because lockscreen wasn't working, please take a look here:

[http://www.tuxgarage.com/2011/10/installing-xscreensaver-in-11-10-ubuntu.html](http://www.tuxgarage.com/2011/10/installing-xscreensaver-in-11-10-ubuntu.html)

---

### Post by Zian on 2012-04-27
Thanks for the help in getting the lock screen to work again.

And yes, I had exactly that problem with XScreenSaver. Thanks for the help with that too.

---

