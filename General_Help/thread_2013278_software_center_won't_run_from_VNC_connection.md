---
title: "software center won't run from VNC connection"
date: 2012-06-30
forum: General Help
---

### Post by AlexBooton on 2012-06-30
Hi,

I posted about this once before but got no replies.

When I try to open the software center gui the window opens but it's blank.  At first there is a "working" indicator (a circle made up of lines) but that goes away and then nothing.

When started from a terminal with software-center I get a lot of messages.

They make no sense to me but maybe someone else will recognize the problem.

Here's the output from software-center:

```
root@mbh:~# software-center
2012-06-30 09:23:58,319 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2012-06-30 09:23:58,319 - dbus.proxies - ERROR - Introspect error on :1.161:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2012-06-30 09:24:23,375 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-30 09:24:23,381 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-30 09:24:23,824 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-06-30 09:24:23,991 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-06-30 09:24:24,007 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
```

Thanks for your help,

AB

---

### Post by amgamgamg3 on 2012-06-30
you must write in the terminal:
sudo apt-get install --reinstall software-center
and then press enter, it resets your software center.
A.Majidzade

---

### Post by choppyfireballs on 2012-06-30
when you connect via vnc out of curiosity are you changing the ui at all. I know when I run vnc on fedora 16 and 17 idefault back to  gnome 2 so if you are defaulting to a different desktop scheme that might have something to do with it.

---

### Post by AlexBooton on 2012-06-30
> **amgamgamg3 said:**
> you must write in the terminal:
sudo apt-get install --reinstall software-center
and then press enter, it resets your software center.
A.Majidzade

Thank you for the feedback.

I tried apt-get --reinstall but it didn't help.

Remember Software Center runs fine from the desktop just not from VNC.  So I think the problem has something to do with VNC.

Thanks,

AB

---

### Post by AlexBooton on 2012-06-30
> **choppyfireballs said:**
> when you connect via vnc out of curiosity are you changing the ui at all. I know when I run vnc on fedora 16 and 17 idefault back to  gnome 2 so if you are defaulting to a different desktop scheme that might have something to do with it.

Hi,

No.  Still running Unity via VNC.

I tried to get a VNC Gnome session but couldn't figure out how to do it.  But that's another story.  :p

---

