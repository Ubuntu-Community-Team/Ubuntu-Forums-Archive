---
title: "Transmission Unable to Update Blocklist"
date: 2011-09-23
forum: General Help
---

### Post by Chonnawonga on 2011-09-23
I've been trying to update my blocklist on Transmission. So far I've tried several blocklists from [http://www.iblocklist.com/lists.php]("http://www.iblocklist.com/lists.php") and other places. I plug in the .gz address and hit "Update", but it always ends up giving me this error: "Unable to update blocklist."

I tried upgrading Transmission to v.2.33, but that made no difference.

Any ideas?

---

### Post by super.roz on 2011-10-04
Same problem here.  Using Transmission 2.13.

---

### Post by ubupirate on 2011-10-04
Try this one?

[http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz](http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz)

---

### Post by jdorenbush on 2011-11-03
> **ubupirate said:**
> Try this one?

[http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz](http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz)

I was having the same problem on Transmission 2.42, but after replacing my current blocklist with the one suggested above I am now able to update the list without any problems. Thanks ubupirate

---

### Post by Chonnawonga on 2011-11-05
Thanks, ubupirate! Works for me too.

For those looking to copy the address, make sure to copy the whole address, not the silly abbreviated version that Ubuntu Forums shows by default.

Here it is again, in unadulterated form:
```
http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz
```

---

