---
title: "Remove Dropbox folder icons"
date: 2011-04-08
forum: General Help
---

### Post by Zilioum on 2011-04-08
I really like the way dropbox integrates with nautilus. The only think I dont like are the folder icons (blue arrows when syncing, green check mark when done) because I feel like they take up to much space. The icon in the task bar is enough for me.

Does anyone know, how I could switch them off? Maybe this could also be done via nautilus itself.

I googled for a bit, but did not find anything usable.

Cheers

---

### Post by mik01aj on 2012-11-15
Yes, I know It's an old question - but there is a simple way to do this:

```
sudo find /usr/share/icons -name emblem-dropbox-* -delete
```

---

