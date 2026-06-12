---
title: "Network Manager Missing on Panel"
date: 2011-02-14
forum: General Help
---

### Post by MikeyDL on 2011-02-14
For some reason when I booted today the network manager icon to disconnect and connect to different wireless networks was missing.  I've read various post and have been unable to resolve this issue.  Here is what I've tried.

1.  Clicking in Add Panel and adding network monitor.  This seems to be not included on the list of choices.

2.  Clicking in Add Panel and click the Add Notification choice.  This didn't seem to add anything to the panel.  

3.  Remove the Notification area and then re-add it.  Did this and not the area is blank except for my dropbox icon.  I don't have the date, logon or logoff dropdown, or network manager icon anymore.  I've rebooted several times.

Any ideas on how to fix this?  I can't connect to my wireless network anymore.  Is there another way to manager wireless connections other then that panel tool?

---

### Post by mrpenguin on 2011-02-14
Is it gone even after you reboot ?
Sometimes on my machine the log off icon on the far right corner is missing but it comes back after I reboot.

---

### Post by MikeyDL on 2011-02-14
Okay so reading up more.  I did the following commands:

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

This basically reset my gnome bar panels back to default.  However, I still don't have the network app icon.

I can open network tooks and look at my wireless device but can't figure out how to get it to connect to my wireless network.

---

### Post by plucky on 2011-02-14
Try ALT+F2 and in the window that opens ```
nm-applet &
```


Good Luck

---

### Post by MikeyDL on 2011-02-14
Okay so getting some progress.  I've got a back USB stick D-Link network adapter and plugged that in and the network panel icon showed up.  I'm guessing that it only shows up if you have a wireless device you need to configure.  I'm guessing that for some reason my laptop wireless card is messed up now so I guess that is a different problem.

But thanks for the tips!  I'll remember the nm-applet & tip in my notes!

---

