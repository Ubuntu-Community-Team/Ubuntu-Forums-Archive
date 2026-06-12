---
title: "rtorrent help needed"
date: 2010-09-23
forum: General Help
---

### Post by alexmack on 2010-09-23
1) although i have the settings set for it to stop seeding at 200% ratio, it doesn't remove the downloads from the client. it just lists them as "completed" instead... how can i have it remove them?

2) how can i make it delete the original .torrent files it used when it's finished?

---

### Post by mobilediesel on 2010-09-23
> **alexmack said:**
> 1) although i have the settings set for it to stop seeding at 200% ratio, it doesn't remove the downloads from the client. it just lists them as "completed" instead... how can i have it remove them?

2) how can i make it delete the original .torrent files it used when it's finished?

For number 2) add this to your .rtorrentrc
```
on_close = remove_fin,"execute=rm,$d.get_tied_to_file="

```

for number 1) I've been trying to find that for almost 2 years.

---

### Post by alexmack on 2010-09-23
i get 

(10:46:41) Deprecated on_* commands, use 'system.method.set_key = event.download.{inserted, erased, ...},

after adding that

---

### Post by mobilediesel on 2010-09-23
> **alexmack said:**
> i get 

(10:46:41) Deprecated on_* commands, use 'system.method.set_key = event.download.{inserted, erased, ...},

after adding that

I'm running rTorrent v 0.8.0
which version are you running?

---

