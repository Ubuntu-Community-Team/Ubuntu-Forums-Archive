---
title: "Unknown Not Responding"
date: 2010-01-23
forum: General Help
---

### Post by Howie Spitz on 2010-01-23
First noticed this window when trying to logout: (I can Logout Anyway of course)
[[IMG]http://imgur.com/qRH8C.jpg[/IMG]]("http://imgur.com/qRH8C.jpg")
 I ran top right after getting this message, nothing stands out. Mass quantities nautilus segfault  error 14  from System Log.
When I login I get spinning cursor (working) and in winlist endless folder icons and arrows that say File Manager. If I click on one (like shooting arcade ducks) then my cursor stops spinning  and CPU calms down.
I suspect recent updates are the cause of it all but I need help sorting it out please. Thank you . Not using compiz when this happens.

---

### Post by rogue_0111 on 2010-01-23
Press "CTRL" + "ESC". It's like task manager in Windowz. There you will be able to locate the culprit.

--

---

### Post by Howie Spitz on 2010-01-24
I've tried both CTRL + ESC and nothing happens to the Unknown Popup. 
It seems to block anything else, terminal, etc. :confused:
Unless I choose Cancel I don't seem to be able to start any other task.

---

### Post by Howie Spitz on 2010-01-24
It seems this is Gnome related. ( I ran a E17 session, KDE session, without login/out problem). Since the File Manager icons are in the bottom panel and gnome panel uses the most CPU in top. So far that seems most likely to me.
Is this persistent nautilus error 14 in System Logs related to the problem? 
Is there different / better way to troubleshoot this logout problem?
Thank you very much for any help.

---

### Post by Howie Spitz on 2010-01-25
After  removing ~/.gconf/apps/nautilus, some updates today , and trying to run a backtrace on nautilus I was able to login to a
 gnome session without the endless loop of File Manager running in winlist.
I was working on filing here:[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/434921](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/434921)
Howie's ~/.xessions-errors
** (nautilus:6042): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension

(nautilus:6042): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (nautilus:6086): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:6086): WARNING **: No marshaller for signature of signal 'DownloadFinished'
What the problem actually was, or how it was fixed I don't know. So mark this [UNSOLVED]

---

