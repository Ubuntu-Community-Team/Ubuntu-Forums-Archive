---
title: "Does Ubuntu or Apache2 have a way to automatically delete temp files?"
date: 2010-08-14
forum: General Help
---

### Post by joesmith1234 on 2010-08-14
I have a PHP script running on my website that can generate temporary images, but if I clean them up right away, then the browser doesn't have time to render them.

Is there some way to make Apache2 delete them after 5 minutes or so?

---

### Post by x1a4 on 2010-08-14
Hi,

Write a script to delete the files then setup a cron job to run the script every 5 minutes.

Add this line (appropriately modified) in /etc/crontab
```

*/5    *    *    *    *    /path/to/tmp_del_script

```

---

