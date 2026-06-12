---
title: "jumpy mouse and erratic keyboard in karmic with Transmission running"
date: 2009-10-30
forum: General Help
---

### Post by ctrlf5 on 2009-10-30
I've encountered some weird behavior. When I start Transmission, my wireless RF keyboard and mouse are erratic. Moving the mouse around the screen is slow, jumpy and at times, unresponsive. Clicks are not recognized. Keyboard strokes take multiple presses to get the expected response as well.

Is anyone else experiencing this? I only get it when running Transmission. Once Transmission is shut down, everything works fine.

---

### Post by geirha on 2009-10-30
What type of internet connection do you have? wireless or wired? I'm thinking maybe the wifi (if you are using it) could be interfering with the signals for your keyboard and mouse. Torrenting can produce alot of activity.

---

### Post by ctrlf5 on 2009-11-01
I have a wireless connection. Also, I have been using the same hardware for previous versions of Ubuntu without issue. It only started happening after I installed Karmic.

---

### Post by P4man on 2009-11-01
> **ctrlf5 said:**
> I have a wireless connection. Also, I have been using the same hardware for previous versions of Ubuntu without issue. It only started happening after I installed Karmic.

try moving your wifi further away from your usb mouse/kn dongle. Also changing the frequency (channel) of the access point can help a lot. I doubt its related to the karmic upgrade, what you are describing sounds very much like a 2.4 GHz interference problem.

---

### Post by ctrlf5 on 2009-11-01
I don't think so. I mentioned in my previous post that this erratic behavior **only** occurs when Transmission is running. Otherwise, the system is fine.

---

### Post by P4man on 2009-11-01
> **ctrlf5 said:**
> I don't think so. I mentioned in my previous post that this erratic behavior **only** occurs when Transmission is running. Otherwise, the system is fine.

tranmission, or any other bittorrent client I bet. Or any other application that establishes 100's of simultaneous connections over your wifi. I also bet if you pause all torrents in tranmission the problem goes away after a few seconds.

You dont have to believe me ( and hey, I might even be wrong), but try changing your wifi channel from one extreme to another. Try channel 1 or 11 or whatever is furthest from your current one.

---

### Post by ctrlf5 on 2009-11-01
Thanks! It worked!

---

### Post by ctrlf5 on 2009-11-10
I spoke too soon. Changing channels nor moving the router doesn't work. It's gotta be a Karmic thing since I had no problem whatsoever when I was running Jaunty.

---

### Post by P4man on 2009-11-10
You'll only convince me this could even be a "karmic" issue rather than a 2.4GHz interference problem if you plug in a wired connection, disable wifi and the problem doesnt go away. Or if you hit the wifi kill switch and the problem doesnt go away almost instantly.

---

### Post by ctrlf5 on 2009-11-10
> **P4man said:**
> You'll only convince me this could even be a "karmic" issue rather than a 2.4GHz interference problem if you plug in a wired connection, disable wifi and the problem doesnt go away. Or if you hit the wifi kill switch and the problem doesnt go away almost instantly.

I'll just follow the other threads on this same issue then. Thanks anyway.

---

### Post by abben on 2010-01-01
I know this is an old thread, but I just wanted to chime in. I have a wired connection, and am getting the same when I use transmission or rtorrent. Also, the same thing happens if I am downloading a lot via wget.

Th sluggishness does not go away after the download is completed.

---

