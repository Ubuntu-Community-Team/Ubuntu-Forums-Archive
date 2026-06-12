---
title: "Deluge won't connect to daemon"
date: 2011-01-17
forum: General Help
---

### Post by zorblek on 2011-01-17
I'm trying to connect the Deluge GTK UI to the daemon running on the same system. This worked just fine previously, but for no apparent reason I can't connect now. I have Deluge set to autoconnect on startup, but it doesn't. If I open the connection manager, it says the daemon isn't running (which isn't true; I checked), and trying to start or connect to the daemon from there does nothing.

I get the following errors from deluge:
```
[ERROR   ] 16:12:11 gtkui:343 Connection to host failed..
[ERROR   ] 16:12:32 gtkui:343 Connection to host failed..
[ERROR   ] 16:12:54 gtkui:343 Connection to host failed..
[ERROR   ] 16:13:15 gtkui:343 Connection to host failed..
[ERROR   ] 16:13:37 gtkui:343 Connection to host failed..
[ERROR   ] 16:13:58 gtkui:343 Connection to host failed..
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.TCPTimedOutError: TCP connection timed out: 110: Connection timed out.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.TCPTimedOutError: TCP connection timed out: 110: Connection timed out.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.TCPTimedOutError: TCP connection timed out: 110: Connection timed out.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.TCPTimedOutError: TCP connection timed out: 110: Connection timed out.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.TCPTimedOutError: TCP connection timed out: 110: Connection timed out.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.TCPTimedOutError: TCP connection timed out: 110: Connection timed out.
[ERROR   ] 16:14:20 gtkui:343 Connection to host failed..
```

If I try to connect with deluge-console, I get this message:
```
Failed to connect to 127.0.0.1:58846 with reason: Connection timed out
```

I'm really puzzled, because I've never had any trouble before. If anyone can help me out, I'd really appreciate it.

---

### Post by Cas07 on 2011-01-22
You should really post this question in our support [forum]("http://forum.deluge-torrent.org/viewforum.php?f=7"). 

If you could include details such as versions and deluged log

---

