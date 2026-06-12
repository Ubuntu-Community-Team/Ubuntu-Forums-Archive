---
title: "8/29 update broke Deluge"
date: 2012-08-29
forum: General Help
---

### Post by KirbySmith on 2012-08-29
Today's Lucid update seems to have broken Deluge.  After the update it would only partially start.  Removal and re-installation using Ubuntu Software Center led to this message upon start-up:

```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 308, in _on_reactor_start
    client.start_classic_mode()
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 563, in start_classic_mode
    self._daemon_proxy = DaemonClassicProxy(self.__event_handlers)
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 436, in __init__
    self.__daemon = deluge.core.daemon.Daemon(classic=True)
  File "/usr/lib/pymodules/python2.6/deluge/core/daemon.py", line 141, in __init__
    from deluge.core.core import Core
  File "/usr/lib/pymodules/python2.6/deluge/core/core.py", line 36, in <module>
    from deluge._libtorrent import lt
  File "/usr/lib/pymodules/python2.6/deluge/_libtorrent.py", line 59, in <module>
    import libtorrent as lt
ImportError: No module named libtorrent
```It seems to need a key part. Any suggestions will be appreciated.  (Observed on Desktop 2 defined below.)

kirby

---

### Post by raja.genupula on 2012-08-29
open synaptic manager and look for the package named as libtorrent and install it from there and try again .

---

### Post by KirbySmith on 2012-08-29
Thanks Raja, but further complexity has reared its ugly head.  Synaptic shows a whole bunch of libtorrents, two of which are installed.

libtorrent11
python-libtorrent
python-libtorrent-dbg
.
.
.
libtorrent-rasterbar5 [installed]
libtorrent-rasterbar6 [installed]
libtorrent-dev
...
libtorrent-ruby1.8
libtorrent-ruby

One might imagine that somehow Deluge has lost its linkage to whichever one it was previously using.  But I will be happy to kill any of these and install one or more others, given a further hint as to which to use.

Or, I suppose I could uninstall both installed libtorrent versions, run update and see what it thinks is broken.

kirby

---

### Post by KirbySmith on 2012-08-29
The experiment failed.  Removal of libtorrent packages did not show up as a missing item in Update Manager, reinstallation of Deluge using Synaptic did not drag in any libtorrent files.  The Deluge UI has the add/subtract +/- buttons grayed out; and preferences still grays out most options.

On the other hand, Deluge doesn't complain about missing libtorrent.

k

---

### Post by KirbySmith on 2012-08-29
Well, there was a cockpit error somewhere.  I reinstalled libtorrent-rasterbar and eventually a startup of Deluge returned full functionality.

I guess this is solved, mysteriously.  I'll tag it solved later when I'm sure of repeatability.  Probably have to do something similar with the other desktop.

kirby

---

### Post by KirbySmith on 2012-08-30
Deluge was not broken on the other desktop, so cockpit error seems most likely.

MYSTERIOUSLY SOLVED

---

