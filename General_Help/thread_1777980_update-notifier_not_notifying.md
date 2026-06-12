---
title: "update-notifier not notifying"
date: 2011-06-08
forum: General Help
---

### Post by jim_deadlock on 2011-06-08
I have Update Notifier enabled in my startup apps and I've checked that update-notifier is actually running, and I have my updates set to check for updates daily and only notify about available updates. However, I never get any notifications despite having updates available. I'm using Unity on 11.04 and I've enabled "all" icons on my top panel. Any ideas?

---

### Post by iclestu on 2011-06-08
> **jim_deadlock said:**
> I have Update Notifier enabled in my startup apps and I've checked that update-notifier is actually running, and I have my updates set to check for updates daily and only notify about available updates. However, I never get any notifications despite having updates available. I'm using Unity on 11.04 and I've enabled "all" icons on my top panel. Any ideas?

lets just make sure you are not actuially MISSING any updates.....

run these in terminal:

```
sudo apt-get update
sudo apt-get upgrade
```If it installed updates then you were missing some. If not, you already had them installed and perhaps there just havent been any since you last did it or perhaps your setup is installing them automatically...

---

### Post by jim_deadlock on 2011-06-08
I regularly get updates and I have to do them manually, I have some there right now and I've been waiting and waiting for the notifier but it never appears.

---

