---
title: "Kopete &quot;hangs&quot; in Kubuntu 10.10"
date: 2010-11-08
forum: General Help
---

### Post by gowaddle on 2010-11-08
I'm running Kubuntu with KDE 4.5.3 and noticed that if I don't have any chat windows open and kopete minimized to the message indicator, it will appear to "hang" and log out all of my accounts.  I sometimes have to do a killall from the command line or restart it.  If I keep at least one chat window open on the desktop of the main Kopete window open, I never have any problems.

My Google-Fu hasn't turned up anything so I thought I'd check if anyone else has had this type of problem?

---

### Post by gowaddle on 2010-11-11
I went back to testing it and selected the icon to show the icon in the panel.  Once I did that, kopete stays logged in and doesn't crash at all.  It's also completely reproducible.

---

### Post by kxmas on 2010-11-21
Thanks for the tip.  This has been aggravating.

---

### Post by Eric Durand-Tremblay on 2011-03-15
I have exactly the same problem with natty 11.04.

If I close the Kopete window, after a while, it is not possible to open it anymore from the system tray message indicator.  The kopete process still run in the background and it lock any new instance of Kopete.

A temporary solution is to killall kopete and to start it again.

Anybody got a hint about this problem ?

---

### Post by fjleal on 2011-04-04
Same problem here running Kopete 4.6.1a on KDE 4.6. I noticed a pattern: having Kopete's main window closed it can be reopened from the Message Indicator applet at any time and I get notified about who logs in/out. It works flawlessly until I chat for the first time. After closing the chat window for my first conversation, Kopete is still running ("ps" shows the process), it is still shown in the Message Indicator applet, but no longer responds to the open command nor does it fire any notifications.

Solution: kill the process and start the application again. :(

---

### Post by orville99 on 2011-06-15
I am having the same issue and it's really frustrating. It has plagued me in both 10.10 and 11.04 (fresh install).

---

### Post by sclaughl on 2011-06-21
I'm experiencing this behavior, too. Does anyone know if this bug has been logged against kopete? I'm going to look into it right now.

--Stuart

---

### Post by sclaughl on 2011-06-21
Found this bug report, which appears to be the same thing we're experiencing: 

[http://bugs.kde.org/show_bug.cgi?id=275271](http://bugs.kde.org/show_bug.cgi?id=275271)

Please vote for this bug!


--Stuart

---

### Post by viziouz on 2011-07-06
I had the same issue and resolved it this way:

In kopete: go to SETTINGS > CONFIGURE > BEHAVIOR > check "show system tray icon"

Kopete version: 1.0.80
KDE version: 4.6.2 on 64bit Kubuntu 11.04

---

