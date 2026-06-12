---
title: "Deluge setup for don't block browser?"
date: 2012-03-12
forum: General Help
---

### Post by ayozito on 2012-03-12
Hey!

Using back the torrents I just figured why I had let use it, the downloads and use the browser at the same time!

I have 10MB ADSL, which configuration should I use in max connections (general, tries/second, partial open...)??

---

### Post by ankspo71 on 2012-03-12
Hi,
I can only give you general advice, I'm using Tixati for torrents.

Are you using a router? Most routers have trouble with too many connections. Using torrents can use up to hundreds of simultaneous connections at a time, and when you try to use a web browser it is blocked because the browser has to wait until the router can give it a new connection. My advice is to use only a small amount of connections in Deluge settings. 

for maximum connections, try 10
for half open connections, try 20 
for maximum connections per second, try 5

You might want to limit your download (and) upload speeds in Deluge because that can cause problems with browsers too. I recommend telling Deluge to use half of your download speed and half of your upload speed.

If this still does not help, then you could try starting deluge with lower priority (a higher nice value). This will give all other applications more priority than Deluge. You can test this by opening a terminal and pasting the following command:
```
nice -n 10 deluge
```

Hope this helps.

---

### Post by ayozito on 2012-03-12
Yes, I know this is problem of router handling connections, thats why I asked for max connections settings.

I just setted that ones you said, lets see how them work.

---

### Post by ayozito on 2012-03-12
I noticed that I had the wrong port opened (cool port test it has that it said that port was opened...), I had 2 numbes swaped, instead a 15 I had a 51 xD

I updated router (TP-Link W8961ND) firmware and configured the right port at deluge, and with default options (200 connections, 50 half, 5 per second) I am navigating ok while I am downloading.

---

