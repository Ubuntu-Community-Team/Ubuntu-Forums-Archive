---
title: "wlan0 bitrate repeatedly reverting to something very low"
date: 2009-08-04
forum: General Help
---

### Post by Furyhunter on 2009-08-04
Something is seriously screwed up.  The bitrate on wlan0 is constantly repeating to something very low, usually in the single digits, regardless of what I set using iwconfig:
```
sudo iwconfig wlan0 rate 54M
```

Rutilt tells me it's 54M for about a second, and then goes back to something random between 1M and 10M.  Always shifting.  But my download speed is ALWAYS limited to 128kB/s.

This has been a problem since 8.10, when I started using Ubuntu.  I am using an RT2500.

---

