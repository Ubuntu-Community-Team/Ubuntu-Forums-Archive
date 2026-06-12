---
title: "Music Player Daemon not lauching at login"
date: 2010-03-16
forum: General Help
---

### Post by marttikoo on 2010-03-16
Hi,

I'm setting up Ubuntu based multimedia PC. I need instructions how to make Music Player Daemon to lauch at login. Tried to put it to startup programs but it still doesnt lauch. Could it be that wlan connection and network drive mount not are not established fast enough for mpd to launch? From terminal mpd launches normally and works perfectly.

Im using 9.10.

---

### Post by Brandon Williams on 2010-03-16
I start mpd as a startup app without a problem. The fact that I'm not connected to the network yet doesn't cause any trouble. It could be the network mount, though. Are there any errors in the mpd.log or .xsession-errors that might help to figure out what the problem is?

---

### Post by marttikoo on 2010-03-17
Hi,

Problem solved. Thank you for guiding me to .xsession-errors (had no clue bout that :)). Issues was caused by incorrcet file permissions in mpd.conf and mpd.log. Also bind_to_address had incorrect value.

Thanks

---

