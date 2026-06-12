---
title: "Software Center Crashes"
date: 2012-01-02
forum: General Help
---

### Post by nasageek on 2012-01-02
I am currently having trouble with Ubuntu software center(in ubuntu 11.10), whenever I try to open it, it starts to load and opens the frame and buttons, but none of the content, then goes gray.  When I try to close it, I have to force quit it.  This all started happening after it crashed trying to install oracle database 11g r2.  I tried to apt-get purge it, and then reinstall it.  After I did this I started it from terminal and continued to crash in the same manner.  Below is the terminal output when it ran.

2012-01-02 12:48:28,347 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-01-02 12:48:53,538 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 406, '_introspect_error_handler')'
2012-01-02 12:48:53,538 - dbus.proxies - ERROR - Introspect error on :1.182:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2012-01-02 12:49:19,476 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-01-02 12:49:19,575 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css

---

