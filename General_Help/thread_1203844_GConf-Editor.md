---
title: "GConf-Editor"
date: 2009-07-03
forum: General Help
---

### Post by Ocean Machine on 2009-07-03
OK, so I really screwed up my Gnome-Do and want to start again from scratch. I removed the packages completely, and deleted the folder from .gconf/apps, but there's still this key in there that's preventing things from working correctly when I reinstall. Of course, it's probably something I did, but I have no idea how to get rid of it. Any help in getting rid of this bugger is appreciated. Here's the screenshot in gconf-editor:

[IMG]http://farm4.static.flickr.com/3155/3686209384_434f7cc089.jpg[/IMG]

---

### Post by jenkinbr on 2009-07-03
Right-click the key and choose 'unset key'.

See if that helps.

---

### Post by Ocean Machine on 2009-07-03
> **jenkinbr said:**
> Right-click the key and choose 'unset key'.

See if that helps.

Well, it disappears, but if I navigate back, it's there again.

---

### Post by Ocean Machine on 2009-07-03
Ahh, ok, I think I got it. I found an entry for that key under /etc/gconf/Mandatory which I deleted. I then reinstalled Gnome-Do and everything's back to normal!

---

