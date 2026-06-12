---
title: "rtorrent won't upload."
date: 2010-07-17
forum: General Help
---

### Post by Akegata on 2010-07-17
I'm trying to set up rtorrent in a useful way, but for some reason I can't get it to seed anything at all, not even when I'm downloading torrents (which works fine).

[Here's my .rtorrent.rc-file.]("http://pastebin.com/bLFVXchu")

netstat tells me this:
```
netstat -apn | grep LIST | grep rtorrent
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:50000           0.0.0.0:*               LISTEN      18745/rtorrent  
tcp        0      0 127.0.0.1:5000          0.0.0.0:*               LISTEN      18745/rtorrent
```

When I try to access port 50000 from an external host through nmap I get this:
```
PORT      STATE SERVICE
50000/tcp open  iiimsf
```

Obviously the port forwarding works fine..so why won't rtorrent upload anything? :(

---

### Post by Akegata on 2010-07-17
Also, disk space in rutorrent is completely broken, it says different values pretty much all the time, sometimes negative values even though I have 2TB free.
That's just a minor annoyance though, unless it's actually related to the seeding problem somehow which I highly doubt.

---

