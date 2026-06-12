---
title: "Ugly Programs While Running as Super-User With Compiz"
date: 2006-06-12
forum: General Help
---

### Post by BitTorrentBuddha on 2006-06-12
Hi, I just installed xgl & compiz cvs this week, I must say I'm truly loving it so far. The only problem I've been experiencing is that any program run as root (update manager most frequently) has the very ugly (in comparison), gnome default theme. It sticks out like a sore thumb, it's not a major issue or anything, but I was just wondering if there were any known fixes for this. Thanks.

---

### Post by blackjack6.21.91 on 2006-06-12
Hey.  I've had the following problem before.  The only problem is I use X and Metacity (the defaults).  The fix is to link your root themes folder to your own themes folder.  So for me the fix was:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by BitTorrentBuddha on 2006-06-12
Thanks a million for the super quick reply and the simple fix! :)

---

