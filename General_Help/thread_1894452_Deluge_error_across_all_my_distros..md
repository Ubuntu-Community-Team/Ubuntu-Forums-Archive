---
title: "Deluge error across all my distros."
date: 2011-12-12
forum: General Help
---

### Post by baillou2 on 2011-12-12
So I've been having this problem for a while. Different things happen depending on whether it's Ubuntu, Mint, Pinguy etc. But this is what's happening with Deluge on Ubuntu 11.10.
I try to open a torrent with Deluge and I get this error message


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py", line 299, in _on_reactor_start
    client.start_classic_mode()
  File "/usr/lib/python2.7/dist-packages/deluge/ui/client.py", line 559, in start_classic_mode
    self._daemon_proxy = DaemonClassicProxy(self.__event_handlers)
  File "/usr/lib/python2.7/dist-packages/deluge/ui/client.py", line 432, in __init__
    self.__daemon = deluge.core.daemon.Daemon(classic=True)
  File "/usr/lib/python2.7/dist-packages/deluge/core/daemon.py", line 136, in __init__
    from deluge.core.core import Core
  File "/usr/lib/python2.7/dist-packages/deluge/core/core.py", line 36, in <module>
    from deluge._libtorrent import lt
  File "/usr/lib/python2.7/dist-packages/deluge/_libtorrent.py", line 59, in <module>
    import libtorrent as lt
ImportError: No module named libtorrent


Any ideas? This has never happened before about a few weeks ago. And all of a sudden none of my distros work with Deluge. Strange.

---

### Post by pretty_whistle on 2011-12-12
Maybe it's the sites where the torrents are from.

---

### Post by baillou2 on 2011-12-12
> **pretty_whistle said:**
> Maybe it's the sites where the torrents are from.

No, this applies to any torrent, including iso's of ubuntu for example.

---

### Post by RealityMaster on 2011-12-12
Not sure but it may be related to this?...

[https://bugs.launchpad.net/ubuntu/+source/deluge/+bug/830782](https://bugs.launchpad.net/ubuntu/+source/deluge/+bug/830782)

---

### Post by Cas07 on 2012-01-10
Was this resolved? 

The error is simply because you do not have libtorrent installed. Installing deluge or deluge-common from apt-get should also install libtorrent for you.

---

### Post by |{urse on 2012-01-10
Straight from the deluge faq

> 
Deluge won't start with a "ImportError: No module named libtorrent" error.

You need to install  libtorrent-rasterbar


[http://dev.deluge-torrent.org/wiki/Faq#DelugewontstartwithaImportError:Nomodulenamedlibtorrenterror](http://dev.deluge-torrent.org/wiki/Faq#DelugewontstartwithaImportError:Nomodulenamedlibtorrenterror).

I had to do this too ;)

---

