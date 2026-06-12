---
title: "rtorrent wont download status is always closed"
date: 2010-10-30
forum: General Help
---

### Post by amsterdamharu on 2010-10-30
I try to download a torrent with rtorrent but whatever torrent file I use the status is always closed. Here is what I see on the screen:
```

                   *** rTorrent 0.8.2/0.12.2 - desk:5560 ***
[View: main]
*  ubuntu-9.10-desktop-i386.iso
* [CLOSED]     0.0 /  690.0 MB Rate:   0.0 /   0.0 KB Uploaded:     0.0 MB
* Inactive:


(19:35:49) Using 'epoll' based polling.
[Throttle  10/ 50 KB] [Rate   0.0/  0.0 KB] [Port: 18914] [Bind 192.168.0.11] [

```

I start rtorrent using the following command:
rtorrent -p 18914-18914 -b 192.168.0.11 2> ~/errors.txt

The errors.txt is empty.

---

