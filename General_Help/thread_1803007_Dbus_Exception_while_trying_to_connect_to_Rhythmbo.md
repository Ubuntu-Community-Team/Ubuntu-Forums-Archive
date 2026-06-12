---
title: "Dbus Exception while trying to connect to Rhythmbox with Python"
date: 2011-07-12
forum: General Help
---

### Post by liricooli on 2011-07-12
Hi Guys, I'm trying to use the Rhythmbox SDK via Dbus in order to write a plugin for rhythmbox. 

i'm running kubunto natty,  Python 2.7.1+. I'm good with python but rather new to linux.

While using the terminal - following this post [these instruction ]("http://fredreh.wordpress.com/2008/02/13/put-rhythmbox-om-the-d-bus/")and using this command:
> dbus-send --print-reply --dest=org.gnome.Rhythmbox /org/gnome/Rhythmbox/Player  org.gnome.Rhythmbox.Player.getPlayingUri 

I'm getting a reply.

When trying to use python, following this code from [this example]("http://unmaintainable.wordpress.com/2006/12/10/controlling-rhythmbox-using-dbus/"):
> #! /usr/bin/env python import dbus  session_bus = dbus.SessionBus()  proxy_obj = session_bus.get_object(     'org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')  player = dbus.Interface(proxy_obj, 'org.gnome.Rhythmbox.Player')  print player.getPlayingUri()

 
I get this Exception:

> Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/python-console/pythonconsole.py", line 393, in __run
    exec command in self.namespace
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I tried various code options but could not understand why I'm not getting reply.

Any help on this would be appreciated.

Thanks,
Liron.

---

