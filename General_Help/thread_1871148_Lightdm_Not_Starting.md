---
title: "Lightdm Not Starting"
date: 2011-10-28
forum: General Help
---

### Post by jim_deadlock on 2011-10-28
I installed a package which had gdm as a dependency, so it switched my system to gdm by default. Then I uninstalled that package and also gdm. However, my computer no longer boots into the desktop - during normal boot process lightdm is started but then stopped, so I think somewhere the setting that chooses which display manager to run has not been properly reset, but I don't know where that setting is. If I boot into recovery mode and then do:

```
sudo service lightdm start
```

... it then starts the desktop normally and everything is fine and dandy. I've tried using bum to set lightdm to start up on boot (see below) but that still doesn't seem to work. Any suggestions?

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/lightdm.gif[/IMG]

---

### Post by jim_deadlock on 2011-10-28
Update: I tried reinstalling gdm, during which a dialog popped up where I had to select which display manager to use (which seemed promising), so I selected lightdm and rebooted but still no joy. I'm still having to log in to the recovery console and start the lightdm service manually. I feel a fresh system install coming on :(

---

### Post by enkay009 on 2011-10-28
The default display manager (lightdm, gdm) is stored in this text file: /etc/X11/default-display-manager

Check the contents of that file. For lightdm it should be:
```
/usr/sbin/lightdm

```

---

### Post by jim_deadlock on 2011-10-28
It just said lightdm so I changed it to /usr/sbin/lightdm and it's fixed! Woohoo! Thanks very much!

---

### Post by nooneelse on 2011-11-03
Same problem, same fix.
For some reason it just write "lightdm" maybe some package or script is misconfigured.

Thanks.

---

### Post by kc8hr on 2013-01-21
> **enkay009 said:**
> The default display manager (lightdm, gdm) is stored in this text file: /etc/X11/default-display-manager

Check the contents of that file. For lightdm it should be:
```
/usr/sbin/lightdm

```
Another lost soul thanks you!

Tim

---

