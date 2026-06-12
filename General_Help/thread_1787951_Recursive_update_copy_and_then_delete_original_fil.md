---
title: "Recursive update copy and then delete original file"
date: 2011-06-21
forum: General Help
---

### Post by KLStringer on 2011-06-21
Every 12 hours I have a cron job that runs 

```

cp -Ru /media/mnt/* /media/recordings

```I'm looking for something similar to run every 6 months that will do a recursive update and then delete any files or folders older than 30 days in the /media/mnt/* path.

Sorry if this has been asked and is easy to do I looked at the man pages for cp and rm but neither have flags to do what I need and I didn't find anything with google, but I'm probably asking it the wrong question.

Thanks in advance for any help.

---

### Post by KLStringer on 2011-06-22
Still looking....

---

### Post by KLStringer on 2011-06-23
Still looking...

---

### Post by LordNeo on 2011-06-23
Delete older files:

[http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/)

---

