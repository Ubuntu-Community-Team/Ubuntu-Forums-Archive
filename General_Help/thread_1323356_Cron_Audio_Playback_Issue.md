---
title: "Cron Audio Playback Issue"
date: 2009-11-11
forum: General Help
---

### Post by avallario on 2009-11-11
I have a 9.04 Jaunty box strip down to console only. I have it running playback of wav files at certain intervals during the day via cron. Here's the cron line:

13,15,35,55 4-21 * * *   root    /usr/bin/play /usr/local/src/public/bagwav.wav

Pretty simple, short one  problem. Only the first five seconds of the file gets played and then it cuts off.

I've ran that same command from the actual command line and it runs just fine no issues. I even tried making an individual cron entry for the user (rewt) that I was logged in as, and it still cuts off for that users entry. 

So bottom line audio plays fine from command line, but not from a cron entry. What gives?

T

---

### Post by avallario on 2009-11-11
bump

---

### Post by avallario on 2009-11-12
bump

---

