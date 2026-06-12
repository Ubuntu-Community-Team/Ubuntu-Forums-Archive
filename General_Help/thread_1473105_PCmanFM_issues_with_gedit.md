---
title: "PCmanFM issues with gedit"
date: 2010-05-04
forum: General Help
---

### Post by brandon1004 on 2010-05-04
When I open gedit through pcmanfm (desktop or window), and then close gedit, a new pcmanfm window appears. It will happen whether I'm using gedit to open a file, or running the gedit desktop file. This happens with some other app's too: gedit, terminal and epiphany. It gets quite annoying when editing a web page.

Some other information:
Ubuntu 10.04 (on both 32 and 64bit)
Created link from /usr/bin/pcmanfm to /usr/bin/nautilus.

Any help would be appreciated, thanks.

p.s. I tired submitting this once, and I'm pretty sure it didn't go through. But if it did I'm already sorry for the double post.

---

### Post by cariboo on 2010-05-05
If the same thing happens on both versions, there may be something wrong with your link.

---

### Post by brandon1004 on 2010-05-05
Both times were a fresh install. I used this to link:
```
sudo ln -s /usr/bin/nautilus /usr/bin/pcmanfm
```

---

### Post by brandon1004 on 2010-05-05
Allright. I've restarted pcmanfm, and there is no bug. But it still happens when I restart the environment. I'm guessing it's a strange argument being passed. So which file is nautillus normally called from at startup? Thanks.

---

### Post by brandon1004 on 2010-05-05
Fixed. Here's how I did it.
1. Opened /usr/share/applications/nautilus.desktop.
2. Commented out all lines after "Type=Application"
I probably don't have to comment out all of them, but I'm much too lazy to figure out which line is causing it.

---

