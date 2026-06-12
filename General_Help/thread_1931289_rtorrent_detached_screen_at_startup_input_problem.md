---
title: "rtorrent detached screen at startup: input problem"
date: 2012-02-25
forum: General Help
---

### Post by piramiday on 2012-02-25
in order to start a rtorrent+screen session at startup, I've put the following line in my /etc/rc.local :

```
su -l myuser -c "screen -d -m rtorrent"
```

after login, I can successfully attach to this screen, but some kind of input problems occurr.
I can press the up/down keys to change the selected torrent etc, the numbers to change tab in rtorrent, I can detach the screen via C-a d, but if I try to start a torrent (C-s) or exit rtorrent (C-q) nothing happens.

this doesn't occur when I start rtorrent normally :

```
screen rtorrent
```

and then detach via C-a d.

any suggestions?
I read other threads about start/stop daemons, but that's not what I want to do.
thank you.

---

### Post by pyroscope on 2012-03-07
You need to disable flow control.

[http://web.mit.edu/gnu/doc/html/screen_14.html](http://web.mit.edu/gnu/doc/html/screen_14.html)

---

### Post by piramiday on 2012-03-07
yep, that was it. thanks a lot! [-o<

---

