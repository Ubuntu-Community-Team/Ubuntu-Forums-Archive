---
title: "Network monitor missing from notification area."
date: 2009-11-01
forum: General Help
---

### Post by Jack Russell on 2009-11-01
This is a weird one.  I had the thing in there, and I had wireless networking working perfectly (this is even with the Broadcom chipset on the HP mini that is giving other people fits).  It was showing me all of the different wireless choices that I could connect to, I had it connected, and I was surfing the web.

But then I was playing with the notification area, and inadvertently removed the icon from the notification area.   And I can't get it to come back.  Reboot doesn't help.

Despite all of this, the network continues to function, and "nm-applet" is still running on the system.  I installed the application "wifi-radar" and that continues to function.

Other people suggest that there is an "Add to panel" entry up there somewhere, but on my box that too is missing.  I have 'preferences", "about", "remove from panel", "move" (greyed out), and "Lock to panel".  Nothing about "Add to panel".  So I don't see how I am supposed to put this thing back.

Is there a config file or symlink somewhere that gets set as things get added and removed from the notification area?  Something I could tweak to get the (*&(*& thing back?

This is with the 9.10 netbook remix distro.

---

### Post by Tahakki on 2009-11-01
Sure you deleted the icon and not the whole notification area?

---

### Post by admelfo on 2009-11-01
Hmm. Yeah, if you right click on your pane, it should give you an option to "Add to Panel," and then you should be able to choose "Notification Area: to add it to the panel. That's where the networking options show up.

---

### Post by Jack Russell on 2009-11-01
> **Tahakki said:**
> Sure you deleted the icon and not the whole notification area?

Other things like the little envelope icon and the time/date are still there.

---

### Post by Jack Russell on 2009-11-01
> **admelfo said:**
> Hmm. Yeah, if you right click on your pane, it should give you an option to "Add to Panel," and then you should be able to choose "Notification Area: to add it to the panel. That's where the networking options show up.

Yeah, I agree - there *should* be an "Add to panel" entry in the context menu, but there isn't any such entry there.  Unless I am right clicking on the wrong thing, but I have tried right clicking on virtually the whole desktop in search of such an entry and have not yet found it.

This is apparently a known bug:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg343789.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg343789.html)

I am mainly interested in the workaround right now.

Or is there some application that I can launch that provides effectively the same functionality?

---

### Post by Jack Russell on 2009-11-02
> **Jack Russell said:**
> 
I am mainly interested in the workaround right now.


I figured it out.  The setting is a per-user setting, and not a system-wide setting.  I logged in under a different account and the network monitor was where it belonged.

So I blew away ~/.gconf and logged out and back in again, and the thing re-appeared, right where it belonged.

Eventually they need to fix this so I can add other things to the panel - I gather there are other things that I could add to the notification area that I might like (such as a CPU monitor).   But not having the network thing up there really cripples using WiFi.

In one unrelated note, this HP mini does have the Broadcom BCM4322 802.11, and I too was having trouble getting it up and going at first.  Ultimately what I did was download the driver from here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and follow the directions and it came right up like a champ (but only as long as you have the WiFi switch on the front turned on :D).  

I am tossing this out mainly because I see **lots** of other people struggling with these things trying to get the WiFi working, and I know how frustrating it can be to be to try and get these things working.  If you do a google search, you find all kinds of different suggestions (some of them apparently only relevant to much older versions of Ubuntu), and it is hard and time consuming to try and figure out which ones are relevant to your situation.

---

