---
title: "Firefox already running"
date: 2009-11-12
forum: General Help
---

### Post by p3car on 2009-11-12
I have an annoying problem with firefox. Everytime I try to start I get an error message "Firefox already running...". I can do 

```
sudo killall firefox
```

and then I can start firefox.
I have also deleted the lock and .parentlock files from the profile directory and that also works. 

If I exit firefox the problem will reappear, and that what irritates me.
I have googled and not found any hints on how to fix this. Should I remove my profile totally?

I was hoping that the upgrade to 3.5.5 would fix this, but it didn't

---

### Post by p3car on 2009-11-12
I cleaned out some Security Devices under Encryption in preferences. I had experimented with getting my usb-dongle for internet banking to work. This seems to be the reason for ff hangning when exiting. 

For now ff exits gracefully and restarts without needing a killall

---

