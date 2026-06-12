---
title: "Remove Envelope From Top Panel"
date: 2011-07-09
forum: General Help
---

### Post by borth92 on 2011-07-09
Hi I am purging the top panel of applets I don't use (social networking, email, etc). I removed all of them via synaptic, but the envelope is still there. It doesnt do anything when i click it but its annoying to still have the icon there.

---

### Post by JRV on 2011-07-09
```
sudo apt-get purge indicator-messages
```

worked for me, in both Lucid and Natty.

---

### Post by nrundy on 2011-07-09
If you prefer a GUI, open USC and search for "indicator-messages" then uninstall. But apt-get faster

---

