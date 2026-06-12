---
title: "network manager keeps disappearing from notification area"
date: 2010-07-08
forum: General Help
---

### Post by amlife on 2010-07-08
Hello 

I have been having issues with 10.4 

1. network manager keeps disappearing from notification area, I would have to run the following command to have it show up again **nm-applet** every-time I log to the system.

2. Audio goes a way all the sudden, I have to log out and log back in to fix this issue. 

Any ideas?

---

### Post by mörgæs on 2010-07-08
I also have various icons disappearing from the top panel. The only solution I found was right-clicking on the panel and adding them. This means that sometimes there are two of each.

I know that this is not elegant, but again it was the only solution I found.

---

### Post by wilee-nilee on 2010-07-08
I had noticed that the top panel in Lucid had sporadic icon problems, if you run this in a terminal it kills and restarts the panel seems to work most of the time, or a logout and restarting x.
```
killall gnome-panel
```

I use maverick now and haven't seen this problem for a couple of weeks.

---

