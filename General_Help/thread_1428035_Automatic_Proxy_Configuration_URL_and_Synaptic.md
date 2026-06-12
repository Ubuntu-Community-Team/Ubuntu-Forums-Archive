---
title: "Automatic Proxy Configuration URL and Synaptic"
date: 2010-03-12
forum: General Help
---

### Post by austin7777 on 2010-03-12
I am unable to download packages from synaptic.  I am at a school that uses an automatic configuration url with a proxy.pac file.  How can I get synaptic to work with this proxy?

---

### Post by gmargo on 2010-03-12
A proxy.pac file should be a text file, I think.  What's in it?

---

### Post by amd is the best on 2010-03-12
I am in the same boat at my job.  We use an auto-proxy setup which works in firefox but not for synaptic.  I setup the system wide proxy settings with my auto-proxy info but no luck.

Any info would be greatly appreciated.

Thanks,
Nick

---

### Post by Hilko on 2011-03-03
I have the same problem. I'm behind a company proxy at work. Opening System->Preferences->Network Proxy and then applying the settings system wide has no effect.

Doing this with the command
```
$ gnome-network-properties
```
gave the following output:
```
cb_make_system_default
reseting proxy http
reset_proxy() returned: 0
Caught remote method exception org.freedesktop.DBus.Python.IOError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/system-service/system-service-d", line 282, in set_proxy
    res = self._clear_apt_proxy(proxy_type)
  File "/usr/lib/system-service/system-service-d", line 246, in _clear_apt_proxy
    for line in open(f):
IOError: [Errno 2] No such file or directory: '/etc/apt/apt.conf'
reseting proxy ftp
reset_proxy() returned: 0
Caught remote method exception org.freedesktop.DBus.Python.IOError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/system-service/system-service-d", line 282, in set_proxy
    res = self._clear_apt_proxy(proxy_type)
  File "/usr/lib/system-service/system-service-d", line 246, in _clear_apt_proxy
    for line in open(f):
IOError: [Errno 2] No such file or directory: '/etc/apt/apt.conf'
reseting proxy https
reset_proxy() returned: 0
Caught remote method exception org.freedesktop.DBus.Python.IOError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/system-service/system-service-d", line 282, in set_proxy
    res = self._clear_apt_proxy(proxy_type)
  File "/usr/lib/system-service/system-service-d", line 246, in _clear_apt_proxy
    for line in open(f):
IOError: [Errno 2] No such file or directory: '/etc/apt/apt.conf'
set_set_to_system_gconf_helper
check_do_system_wide
  system wide HTTP: 
  system wide HTTPS: 
  system wide FTP: 
  no user HTTP
  no user FTP
  no user HTTPS

```

I really hope someone can help with this.

---

### Post by dudkosk on 2011-07-29
My workaround:
Get address of pac file(for example from your browser preferencies), for example it is [http://addressofpac.company.com/proxy.pac](http://addressofpac.company.com/proxy.pac)
Then download it by 'wget [http://addressofpac.company.com/proxy.pac](http://addressofpac.company.com/proxy.pac)'.
Open it, find proxy address with port number, for example ''proxy.company.com:3128" and put it manually into Synaptic->Preferencies->Network.
I thinks that this configuration doesn't change too often, so you could be happy with this solution for a longer time.

---

### Post by dudkosk on 2011-08-16
As I read somewhere at this forum:
[HTML]echo 'Acquire::http { Proxy "http://user:password@address:port"; };' | sudo tee /etc/apt/apt.conf.d/02proxy[/HTML]

---

### Post by rocker2344 on 2011-12-16
mine does not show the file location.
Set to Auto url in network proxy, and apply. What am i supposed to do from here?

---

