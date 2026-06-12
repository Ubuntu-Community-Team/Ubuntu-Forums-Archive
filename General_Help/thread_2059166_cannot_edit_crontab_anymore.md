---
title: "cannot edit crontab anymore"
date: 2012-09-17
forum: General Help
---

### Post by tanoloco on 2012-09-17
Hello,

I was playing around cron and the following command
```
crontab -e
```
worked fine I think.
Then I installed gnome-schedule and didn't like it too much ..
so I removed it and run again
```
crontab -e
```
but nothing was shown, while I had a default crontab file before
and then I noticed that the above command opened a temporary file instead like
```
File: /tmp/crontab.UHzZnP/crontab
```
I tried to edit it with nano, but when I save it of course nothing is changed on my system because its a temporary file.

I searched for /etc/cron.allow or /etc/cron.deny but they don't exist.
What can be changed installing gnome-schedule and how can I turn my system back in order to be able to use crontab -e again?

Thank you for any suggestion

---

### Post by rukiaEnix on 2012-09-17
What happens if you type this command?

```

sudo /etc/init.d/cron restart

```

---

