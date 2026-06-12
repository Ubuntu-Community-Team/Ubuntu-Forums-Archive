---
title: "wireless disconnects but still shows as connected"
date: 2011-05-18
forum: General Help
---

### Post by rimmmer on 2011-05-18
Hi there. Have  an Asus K52 running natty 64, for some reason my wireless disconnects  at seemingly random intervals, sometimes 5 minutes sometimes 5 hours,  however the system still thinks it's connected and therefore doesn't  reconnect. I am running the latest toastmanmod tomato firmware on the  router. It really has me stumped thus why I'm here, does not affect any  of my other devices connected to the wifi and has only affected the  laptop since moving to natty.

I know I've posted elsewhere but that has yielded no replies, so i thought I'd try again in the general section.

---

### Post by aschweig on 2011-05-18
I had some wireless disconnect problems -- I don't know if my experience is the same as yours but it might be a starting point.


[http://ubuntuforums.org/showthread.php?t=1753298](http://ubuntuforums.org/showthread.php?t=1753298)

---

### Post by varunendra on 2011-05-19
> **aschweig said:**
> I had some wireless disconnect problems -- I don't know if my experience is the same as yours but it might be a starting point.


[http://ubuntuforums.org/showthread.php?t=1753298](http://ubuntuforums.org/showthread.php?t=1753298)
+1

It is most often a driver issue. If you also have RTL8191 adapter, try what aschweig suggested. If you are not sure, post the output of:
```
sudo lshw -C network
```

---

