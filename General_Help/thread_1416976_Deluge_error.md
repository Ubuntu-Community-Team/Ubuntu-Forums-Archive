---
title: "Deluge error"
date: 2010-02-26
forum: General Help
---

### Post by arnab_das on 2010-02-26
I'm getting the following error while starting deluge. this happened after i updated it to a more recent version.

```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 275, in _on_reactor_start
    client.start_classic_mode()
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 531, in start_classic_mode
    self._daemon_proxy = DaemonClassicProxy(self.__event_handlers)
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 408, in __init__
    self.__daemon = deluge.core.daemon.Daemon(classic=True)
  File "/usr/lib/pymodules/python2.6/deluge/core/daemon.py", line 138, in __init__
    self.core = Core()
  File "/usr/lib/pymodules/python2.6/deluge/core/core.py", line 82, in __init__
    sys.exit(1)
NameError: global name 'sys' is not defined

```

this is the screenshot: [[IMG]http://img534.imageshack.us/img534/4671/screenshot001hn.png[/IMG]](http://img534.imageshack.us/i/screenshot001hn.png/)

i have tried removing, purging etc. nothing worked so far, kindly help.

---

### Post by OldWisejoe on 2010-02-27
Have the same problem. It happened yesterday.

[IMG]http://img714.imageshack.us/img714/7964/90852089.png[/IMG]
Content of error:
[B]Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 275, in _on_reactor_start
    client.start_classic_mode()
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 531, in start_classic_mode
    self._daemon_proxy = DaemonClassicProxy(self.__event_handlers)
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 408, in __init__
    self.__daemon = deluge.core.daemon.Daemon(classic=True)
  File "/usr/lib/pymodules/python2.6/deluge/core/daemon.py", line 138, in __init__
    self.core = Core()
  File "/usr/lib/pymodules/python2.6/deluge/core/core.py", line 82, in __init__
    sys.exit(1)
NameError: global name 'sys' is not defined[/B]

System:

[IMG]http://img638.imageshack.us/img638/7480/92538220.png[/IMG]
I think, that problem is about python's libs.

---

### Post by OldWisejoe on 2010-02-28
Anybody has same problem? :evil:

---

### Post by arnab_das on 2010-02-28
> **OldWisejoe said:**
> Anybody has same problem? :evil:

btw i resolved the problem by completely removing deluge alongwith configuration files etc. next i reinstalled it.

working fine as of now.

---

### Post by OldWisejoe on 2010-02-28
> **arnab_das said:**
> btw i resolved the problem by completely removing deluge alongwith configuration files etc. next i reinstalled it.

working fine as of now.
it doesn't help for me (

---

### Post by arnab_das on 2010-03-01
> **OldWisejoe said:**
> it doesn't help for me (

try installing delgue from getdeb.net

[http://www.getdeb.net/software/Deluge](http://www.getdeb.net/software/Deluge)

---

### Post by bluephoenix47 on 2010-03-06
I was getting the same error, and after looking through the source code where the error occurred, I find:
       ```
# We must depend on libtorrent >= 0.14.9 due to over-downloading bug    
        if lt.version < "0.14.9":
            log.error("This version of Deluge requires libtorrent >= 0.14.9.")
            sys.exit(1)
```It looks like the most recent version, 1.21, requires libtorrent 0.14.9 or above, however, the most recent version in the repository is 0.14.6 (for xubuntu 9.10 anyway).  Although, what's causing the error appears to be a missing import sys, it shouldn't get used if you have libtorrent .14.9.  If you really want to be complete, you could add to follow to ./deluge/core/core.py before building:
import sys

I did the following:
```

Build and install deluge from source:
<install dependencies. see README in deluge archive>
    python setup.py build
    sudo python setup.py install
Build and install libtorrent:
    ./configure --enable-python-binding --with-boost-python=boost_python-mt-py26
    make
    sudo make install
    cd bindings/python
    python setup.py build
    sudo python setup.py install --install-layout=deb

```You can get the most recent version of libtorrent from:
[http://code.google.com/p/libtorrent/downloads/list](http://code.google.com/p/libtorrent/downloads/list)
Other references
[http://www.rasterbar.com/products/libtorrent/python_binding.html](http://www.rasterbar.com/products/libtorrent/python_binding.html)
[https://bugs.launchpad.net/ubuntu/+source/libtorrent-rasterbar/+bug/335741](https://bugs.launchpad.net/ubuntu/+source/libtorrent-rasterbar/+bug/335741)

---

### Post by Cas07 on 2010-03-12
There is a much simpler way by using the official Deluge PPA (Latest v1.2.1): [https://launchpad.net/~deluge-team/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~deluge-team/+archive/ppa?field.series_filter=karmic)


Note: getDeb seems to have the previous 1.2.0 Deluge version.

---

