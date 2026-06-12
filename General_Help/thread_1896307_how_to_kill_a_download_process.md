---
title: "how to kill a download process"
date: 2011-12-16
forum: General Help
---

### Post by seminal on 2011-12-16
Hi, a download has hung and it keeps trying to download when I restart the software center.  Also, I can't figure out which process it is in sys monitor.

How do you kill a download?  

pgrep foo

kill -s KILL foo?  #What would foo be?

Thanks

---

### Post by lechien73 on 2011-12-16
Hi, I don't think that the download is a separate process. What has probably happened is that the download is stuck somewhere in the cache folder.

You could try the following: Close the software centre, then open a terminal window and type:

```
mv ~/.cache/software-center ~/
```

Re-open the software centre and see if the download has stopped.

---

