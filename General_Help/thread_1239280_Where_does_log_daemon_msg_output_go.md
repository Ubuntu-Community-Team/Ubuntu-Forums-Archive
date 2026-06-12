---
title: "Where does log_daemon_msg output go?"
date: 2009-08-13
forum: General Help
---

### Post by nr0mx on 2009-08-13
MPD is supposed to run as a service at bootup, but doesn't. It works fine when run normally (e.g sudo /etc/init.d/mpd start). I can't see any error messages either. I added some extra log_daemon_msg messages and rebooted, and can't still see the messages I added in log files at /var/log. 

Where does this output go? How do I debug why MPD doesn't run? 
The links look alright to me:

$ ls -ltra | grep mpd
lrwxrwxrwx   1 root root    13 2009-08-10 16:58 S30mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root    21 2009-08-12 23:57 S20mpdscribble -> ../init.d/mpdscribble

---

