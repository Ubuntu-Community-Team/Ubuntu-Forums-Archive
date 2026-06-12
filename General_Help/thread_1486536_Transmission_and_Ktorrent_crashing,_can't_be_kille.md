---
title: "Transmission and Ktorrent crashing, can't be killed"
date: 2010-05-17
forum: General Help
---

### Post by teewikit on 2010-05-17
I'm running Netbook Edition and everything was working great until yesterday. I was downloading a few torrents with Transmission, when the window stopped responding. I closed it, but a zombie process remained. I tried to kill it through System Monitor, then I tried kill -9, but it wouldn't go away no matter how many times I did this.

I rebooted my computer then restarted Transmission, and it happened again after a couple minutes. Reinstalling Transmission didn't help. I installed ktorrent, and now I'm having the same problem with it too.

Does anyone have any idea as to what might cause this or how I could go about fixing it?

---

### Post by Timtro on 2010-05-18
If kill -9 doesn't work, the best I can say is to try deluge :)

---

### Post by Timtro on 2010-05-18
I don't know about ktorrent, but perhaps these are all front ends for rtorrent. You could try reinstalling that, but I don't have high hopes for that solution.

---

### Post by teewikit on 2010-05-20
Deluge works great, and the UI never slows down for a second. Thanks for pointing it out.

---

