---
title: "All applet icons in system indicator area are gone"
date: 2010-05-22
forum: General Help
---

### Post by anuragji on 2010-05-22
I just spent the better part of the last hour trying to figure out what happened and wanted to post this as it may save somebody else's time :)

I had to reboot my laptop after it froze and upon restarting ALL applet icons in the notification where missing: network manager, battery indicator, volume applet, etc.

In many forum posts the first suggested solution is to check whether the NOTIFICATION APPLET itself is added to the panel. Certainly a good idea, so to do that right click on the panel and add the NOTIFICATION AREA to the panel. You can tell whether it is present when you see the dotted line in the panel. But in my case the notification area was still there, so that did not change anything.

Other posts suggested that you need both the Notification applet and the INDICATOR applet. I had the indicator applet disabled to begin with so I was almost certain that this was not the case.  I tried that, no change.

I was able to start all the applets from a terminal window, but as soon as I the terminal, the applet closed as well.

Looking through countless other posts I came across the brilliant suggestion and solution!

When you see the login screen make sure that the type of session is set to GNOME. If it is set to **Failsafe GNOME** the applets may not show up and sure enough that was the case for me!

---

