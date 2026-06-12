---
title: "indicator-applet-complete doesn't save settings"
date: 2011-11-07
forum: General Help
---

### Post by kedmond on 2011-11-07
Hello,
    I'm using Ubuntu 11.04 on a Dell Latitude E6400.

    I've found that the Indicator Applet Complete doesn't save my settings.  For example, when I login the "Indicator for VirtualBox" is no longer there so I have to launch it again.  This didn't use to be the case.  Also, and more annoying, when I go to Time and Date settings, under the "Clock" tab, I'll hit "Weekday" under the "In the clock, show:" header.  This has absolutely no effect and my settings aren't saved.

    So I'm assuming somehow my settings aren't being saved.  Does anyone else have this problem?  How do I fix it?  Thanks!


Update: Also, the Empathy chat client doesn't save my preferences either.  For example, if I reboot Ubuntu, I have to tell Empathy to turn off notifications and also change the theme.  It will never save these settings.  I assume it's related to why the Indicator Applet cannot save my settings.


Update 2:  I found a solution here: [http://askubuntu.com/questions/49766/unity-launcher-does-not-remember-favorites](http://askubuntu.com/questions/49766/unity-launcher-does-not-remember-favorites)

Basically, dconf is needed by Ubuntu to save settings, but it's not a built in requirement.  Strange.  Anyway, a manual install, reinstall, and then relogin fixed it all.

---

