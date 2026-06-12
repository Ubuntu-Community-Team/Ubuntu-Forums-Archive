---
title: "Battery Icon In Panel Does Not Change Or Give Low Battery Warning"
date: 2012-09-02
forum: General Help
---

### Post by bluebrave on 2012-09-02
I recently upgraded from 10.04 to 12.04 Precise (first point release) on my laptop (an MSI machine).  I've resolved several minor issues but can't figure one out and have searched hear and on google to no avail (hope I didn't miss a post somewhere).

Here is the problem I am facing:

The battery status icon in the panel:
1. The icon does not change when the power cord is plugged in or unplugged (the icon remains a battery if that was the power source on boot but won't change if I plug in the power adaptor and visa-verse).

2. The battery indicator does not give me a low battery warning or alert (ubuntu just shuts down with no onscreen warnings).  Under 10.04, I did the the low battery warnings before shut down.

While searching, I've only found questions about the icon being completely missing and reporting the battery critically low when it is not but nothing like my issue.  This came closest and may be related: [http://ubuntuforums.org/showthread.php?t=1966671](http://ubuntuforums.org/showthread.php?t=1966671) (I also have a blank in the dropdown but the icon is present in my panel - it just isn't fully functional).

I did, however, notice that gconf-editor under "apps, gnome-power-manager", there were no notification settings (also using dconf-editor the icon policy is missing but is present under gconf-editor under "ui").  Not sure if that matters or not, however.

I am currently using gnome-classic but noticed the same icon issue in Unity (not sure if unity also has the no low battery warning problem, however).  I have NOT enabled hibernation as I don't use it but wonder if that has an influence or not.

Any ideas?  Is the missing icon-policy the problem? Will it help if I enable hibernation?  Is it a known bug and I just need to wait for the next update?

---

### Post by bluebrave on 2012-09-07
Bump...

Despite updating Ubuntu with some recently released updates, the battery / power manager icon still won't change nor track usage (it shows full even when being used or when almost drained).  Any help onthis would be greatly appreciated.
:confused:

---

### Post by oxf on 2012-09-07
I can't answer your specific question, sorry. However, there does seem to be a general ongoing problem with the reporting of battery status that has not been resolved. I've read all sorts of comments about it. So I suspect it's not the Icon itself thats the problem.

I've had issues for ages on seperate machines with the status not being reported and also the issue with it shutting down because of low battery when its not.

Good luck!

Veronica

---

### Post by bluebrave on 2012-09-07
> **oxf said:**
> I can't answer your specific question, sorry. However, there does seem to be a general ongoing problem with the reporting of battery status that has not been resolved. I've read all sorts of comments about it. So I suspect it's not the Icon itself thats the problem.

I've had issues for ages on seperate machines with the status not being reported and also the issue with it shutting down because of low battery when its not.

Good luck!

Veronica

Thanks for the sympathy.  It's at least nice to know it isn't just me.  Sorry you've had long term problems with this. My old 10.04worked like a charm on battery status, maybe I was spoiled. ;)

---

