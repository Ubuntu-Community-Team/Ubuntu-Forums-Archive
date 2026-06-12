---
title: "Deluge web interface?"
date: 2009-10-05
forum: General Help
---

### Post by Owosso on 2009-10-05
I'm currently using an old computer as a file server, and I have Deluge installed on it for torrenting. I'm accessing it through the web interface (port 1337) to add and monitor the torrents remotely, but I'm having a problem. It only works about half the time. The other half it gives me the following error:
```
--Deluge Error--
DBusException : org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
path : /index
file : /var/lib/python-support/python2.5/dbus/connection.py in call_blocking, line 606

--Input--
<Storage {}>

--Versions--
WebUi : rev.172
Python : 2.5.2 (r252:60911, Jan  4 2009, 17:40:26) 
[GCC 4.3.2]
dbus:0.82.4

--Traceback--
  File "/usr/share/deluge/plugins/WebUi/lib/webpy022/webapi.py", line 304, in wsgifunc
    result = func()
  File "/usr/share/deluge/plugins/WebUi/lib/webpy022/request.py", line 131, in <lambda>
    func = lambda: handle(inp, fvars)
  File "/usr/share/deluge/plugins/WebUi/lib/webpy022/request.py", line 61, in handle
    return tocall(*([x and urllib.unquote(x) for x in args] + fna))
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 151, in deco
    return func(self, name) #ok, continue..
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 135, in deco
    res = func(self, name)
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 168, in deco
    return func(self, name)
  File "/usr/share/deluge/plugins/WebUi/deluge_webserver.py", line 102, in GET
    for torrent_id in ws.proxy.get_session_state()]
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
```Some background info: I've forwarded the appropriate ports on my router, and I've been able to access the Deluge web interface before. I've also been able to access SFTP and transfer files. I haven't changed any settings since then.

Any help would be appreciated.

---

### Post by lovinglinux on 2009-10-05
I don't know about the error, but you should try to use the remote gtk, available in Deluge. It's way much better than any webui, since it's like running Deluge on your own machine.

---

