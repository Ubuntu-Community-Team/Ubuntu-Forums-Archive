---
title: "How do I create a torrent file in terminal,  I'm at a loss."
date: 2009-07-12
forum: General Help
---

### Post by MechaMechanism on 2009-07-12
SOLVED

I have Transmission-Daemon and Transmissioncli and Transmission-Remote, version 1.72.  I can not seem to figure out how to make a torrent file from both a specific file as well as a dir.  Transmissioncli just keeps giving me blank files.  How does Ubuntu make their ISO torrent files?

---

### Post by rampageoberon on 2009-07-12
Hi there, you might want to try the application createtorrent ([www.createtorrent.com](www.createtorrent.com)). This is a command line utility.

Hope this helps

---

### Post by geirha on 2009-07-12
```

transmissioncli -n myfile -c "Some comment" -a http://tracker.url/announce myfile.torrent
transmissioncli -n mydir/ -c "Some comment" -a http://tracker.url/announce mydir.torrent

```

---

### Post by MechaMechanism on 2009-07-13
> **rampageoberon said:**
> Hi there, you might want to try the application createtorrent ([www.createtorrent.com]("http://www.createtorrent.com")). This is a command line utility.

Hope this helpsTook a look at it and looks good, but I would rather use Transmission.  Thanks anyway.  Wonder why no one ever bothered to package it for the Debian based distro's.

> **geirha said:**
> ```

transmissioncli -n myfile -c "Some comment" -a http://tracker.url/announce myfile.torrent
transmissioncli -n mydir/ -c "Some comment" -a http://tracker.url/announce mydir.torrent

```Ah okay.  I had things turned around and missing the filename on the end.  Thank you.

---

