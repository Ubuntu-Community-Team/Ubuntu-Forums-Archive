---
title: "Gwibber - can't run UI"
date: 2011-04-28
forum: General Help
---

### Post by onemanclapping on 2011-04-28
Hey,

I don't really know when did this problem start, but Gwibber stopped working when I try to run it. Gwibber-service runs fine and I get the notifications, but if I try to run Gwibber on the console, here's what happens:

```
onemanclapping@onemanLinus:~$ gwibber
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 87, in <module>
    client.Client()
  File "/usr/lib/python2.7/dist-packages/gwibber/client.py", line 623, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.7/dist-packages/gwibber/client.py", line 71, in __init__
    self.setup_ui()
  File "/usr/lib/python2.7/dist-packages/gwibber/client.py", line 251, in setup_ui
    self.stream_view.set_state(streams)
  File "/usr/lib/python2.7/dist-packages/gwibber/gwui.py", line 410, in set_state
    self.update()
  File "/usr/lib/python2.7/dist-packages/gwibber/gwui.py", line 397, in update
    self.messages.update(self.navigation.selected_stream)
  File "/usr/lib/python2.7/dist-packages/gwibber/gwui.py", line 751, in update
    self.messages = self.message_view.render([selected_stream], count)
  File "/usr/lib/python2.7/dist-packages/gwibber/gwui.py", line 774, in render
    msgs = json.loads(self.model.streams.Messages(streams[0]["stream"] or "all", streams[0]["account"] or "all", time, streams[0]["transient"] or "0", streams[0].has_key("recipient") and streams[0]["recipient"] or "0", orderby, order, limit))
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
onemanclapping@onemanLinus:~$ 

```

Any ideas? I'm using 11.04 updated from 10.10.

Thanks in advance.

---

### Post by FrancoNero on 2011-05-08
also no luck in starting gwibber

---

