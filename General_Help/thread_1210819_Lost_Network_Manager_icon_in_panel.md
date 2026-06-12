---
title: "Lost Network Manager icon in panel"
date: 2009-07-11
forum: General Help
---

### Post by 1500 on 2009-07-11
I lost the icon while playing and do not know how to get it back.  This is the stacked set bars icon with a wireless connection.  The 'Network Connections' icon copied from System>Preferences is not the same.
Something running during startup used to set this icon.  Now it does not.
My wireless connects and works fine.  I just would like to know how to get the icon back.

Thanks in advance.

---

### Post by Gamfrek on 2009-07-11
The same thing happened to me, so I started over... *HINT* *HINT*

:guitar:

---

### Post by steveneddy on 2009-07-11
Try restarting to see if that fixes the issue.

If not, run in terminal:

```
nm-applet
```

If this starts the applet, then go to 

System --> Preferences --> Sessions

and look for the Network Manager listing and make sure it is checked. If not checked then check the box and save, then restart.

If it's not there (highly unlikely) then just add a new listing, name it Network Manager and the launcher will read

```
nm-applet --sm-disable
```

Good luck, we're all counting on you.

---

### Post by Chronon on 2009-07-12
I accidentally removed a Notification Area applet and lost this and several other icons.  Understandably, rebooting didn't help.  After re-adding Notification Area applet I recovered the NetworkManager Applet as well as some other applets I had lost.

---

### Post by 1500 on 2009-07-13
The reply on the Notification Area applet did the job.  Thanks.  it took me awhile to realize that those 3 little dashes represent an applet.  The wireless bars icon is somehow attached to that.
I tried the items of post #3 with no luck.

---

### Post by decoherence on 2009-07-13
The wireless bars icon (aka nm-applet) is attached to the notification area as well as the system update tool, calendar alarms, etc. Basically, anything that would qualify as a notification should go in there.

Not certain why the instructions in post #3 didn't work for you, even without the notification area. I use nm-applet without the notification area all the time, outside of the standard ubuntu desktop. Maybe it's a gnome thing...

---

### Post by Noo 2 Ubuntoo on 2009-08-20
Wow!!:D:D:D:Thanks Chronon. I accidentally deleted the notification area a couple of days ago without realising it and thought I'd just lost Network manager icon, although I knew it was still in the background. 

I never realised the 3 dashes (that I hadn't noticed were missing from my panel) were the notification area applet until 1500 said so. Then 2 days of scouring the forums came to an end in about 10 seconds and 3 clicks on the mouse - Gnome network manager icon back and evolution calendar reminders appeared again.

Easy when you know how and a big Thankyou to you guys.:):):)

---

