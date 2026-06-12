---
title: "Add entry to cron using python?"
date: 2012-06-29
forum: General Help
---

### Post by LuniTux on 2012-06-29
Hello,

Is there a way to add an entry to a cron file using python **without** sudo? I can do it using python-crontab but I want to be able to do it without any add-on programs if possible.

Thanks,

---

### Post by LuniTux on 2012-07-02
Hello myself,

I have found a solution:




```
import os

os.system("crontab -l > /tmp/curcronfile.txt")

os.system("echo '* * * * *	myscript.sh' >> /tmp/curcronfile.txt")

os.system("crontab < /tmp/curcronfile.txt")

os.system("rm /tmp/curcronfile.txt")
```

---

