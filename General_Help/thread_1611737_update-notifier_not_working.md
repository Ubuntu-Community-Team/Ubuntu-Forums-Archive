---
title: "update-notifier not working"
date: 2010-11-02
forum: General Help
---

### Post by Steeperton on 2010-11-02
Update from 10.04 to 10.10 (both 64bit), and since the change, update notifier is no longer working. 

I've reinstalled the update-notifier package, it's on checking daily, but still no automatic update - I have to manually run it.

Any ideas?

And I have run gconftool as below to get it to notify "properly", but it still doesn't work/check for updates. It is in start up programmes, and is currently running.

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Thanks!

---

