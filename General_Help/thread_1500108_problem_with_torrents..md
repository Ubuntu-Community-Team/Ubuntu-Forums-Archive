---
title: "problem with torrents."
date: 2010-06-02
forum: General Help
---

### Post by Grace_11 on 2010-06-02
when i start to download with torrents i cant able browse the web through the firefox, chrome. :(
i have 1 more problem i cant able to watch youtube videos. :(
what to do?

---

### Post by lovinglinux on 2010-06-02
You need to limit the torrent client UPLOAD limit to 80% of your UPLOAD bandwidth limit, otherwise it will clog your network and cause such problem with other applications.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by Grace_11 on 2010-06-03
i have done that.
but same problem still persisting.
i have this problem in windows xp too :(

---

### Post by Oolongtea on 2010-06-03
Do you just have problems viewing youtube videos in Chrome?

---

### Post by Spr0k3t on 2010-06-03
What is your ISPs upload speed and what is your upload limit set to in your torrent software?  For me, I use 90% of my upload bandwidth at offpeak (when I am not using the computer at all) and only 10K all other times.

---

### Post by lovinglinux on 2010-06-03
> **Grace_11 said:**
> i have done that.
but same problem still persisting.
i have this problem in windows xp too :(

See my tutorial for other settings recommendation.

For the YouTube problem, install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

BTW, is advisable to create a thread for each problem, since they are not related.

---

### Post by Grace_11 on 2010-06-03
thanks
just installed that add-on now able to watch videos.

---

### Post by Grenage on 2010-06-03
> **Grace_11 said:**
> when i start to download with torrents i cant able browse the web through the firefox, chrome. 

If the upload is capped, the most common cause is a cheap router.  Torrent clients generally try and establish hundreds of connections by default; knocking this down to about 40 can make a massive difference.  A lot of generic home routers can't handle the amount of connections.

---

### Post by Grace_11 on 2010-06-03
> **Grenage said:**
> If the upload is capped, the most common cause is a cheap router.  Torrent clients generally try and establish hundreds of connections by default; knocking this down to about 40 can make a massive difference.  A lot of generic home routers can't handle the amount of connections.

i have set upload speed to 25K.
stil same problem in both ubuntu & windows.

---

### Post by Grenage on 2010-06-03
I'm talking about connections, not speed; you can customise that in the config.

---

