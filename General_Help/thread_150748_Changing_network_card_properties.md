---
title: "Changing network card properties"
date: 2006-03-26
forum: General Help
---

### Post by danzat on 2006-03-26
Hi,
I have this thing about my home network that my network card would only work at 10Mbps Half-Duplex. I don't mind this problem and don't really care to fix it right now.

What does bother me, is that Ubuntu forces the card to work at another profile, which causes my network connection to be broken.
I've managed to change those options with:
```
sudo mii-tool -F 10bateT-HD eth1
```
I'm afraid however that this change will only apply to this session.

What i'm asking is, how can i make this change permanent? is there any config file?

---

