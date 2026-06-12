---
title: "How do I configure conky to show wlan down/up data"
date: 2009-07-29
forum: General Help
---

### Post by cody7002002 on 2009-07-29
Currently my conky config monitors how much im uploading/downloading and has a graph along with it. It only monitors this when i'm plugged into my wired connection. What do I have to do so that it will monitor my wireless connection?

---

### Post by exjinn on 2009-07-29
```
Down: ${downspeed wlan0} kb/s
Up: ${upspeed wlan0} kb/s
```

Change wlan0 to the name of your wireless connection if it's not the same. 
Add to your conky config. See the screen shot below. 
[URL="http://jinnfire.info/Screenshot-12a.png"]
[IMG]http://jinnfire.info/Screenshot-12b.png[/IMG][/URL]

---

