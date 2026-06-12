---
title: "Help with creating a cronjob that runs every hour"
date: 2012-07-11
forum: General Help
---

### Post by andreas21 on 2012-07-11
hi, i have update.txt file with perl script, and i want to use crontab to schedule that file run every 1 hour. how can i do that? please help!!!!:D

---

### Post by SeijiSensei on 2012-07-11
If you can run the file under your own username, i.e., it doesn't require root privileges, create a "crontab" for yourself using "crontab -e".  By default, you'll get the vim editor.  If you have another editor you prefer, like nano, do this:

```

export EDITOR=nano
crontab -e

```

Now place this line in the editor:

```
0 * * * * /path/to/your/script
```

That will run the script at the top of every hour.  When you save the file and exit the editor, the file will be placed in the root-owned directory /var/spool/cron in a file whose name matches your username.

If the script requires root privileges, use "sudo crontab -e" to place the file in root's crontab, /var/spool/cron/root.

---

