---
title: "NAS not unmount in shutdown - shutdown blocked"
date: 2012-01-06
forum: General Help
---

### Post by Saubazi on 2012-01-06
I have this problem with my laptop. I am mostly running it with WLAN and there already with boot mounting an NFS from NAS was a bit of a theater but I managed to fix this with some scripting that checks availability of net and NAS and mounts - I did this over cron.

However, my main problem is now unmounting the NAS. If I do not do this before shutdown the machine always hangs at "killing all remaining processes" or something like that - I can only shutdown by pressing the powerbutton long enough. I have tried inserting a similar script on rc6.d but to no avail and now I am gradually running out of tricks.

---

