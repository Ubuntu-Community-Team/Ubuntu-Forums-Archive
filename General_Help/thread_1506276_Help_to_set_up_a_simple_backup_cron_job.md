---
title: "Help to set up a simple backup cron job"
date: 2010-06-10
forum: General Help
---

### Post by ourmartin on 2010-06-10
Hi

OK, I must be doing something elementary wrong. I'm trying to set up a simple backup script with cron.

In "crontab -e" (and sudo crontab-e - I tried both) I enter "0 22 * * * /home/USERNAME/.backup.sh", with the hope that it will run the script at 10pm each day. The srcipt work fine if I run in a terminal. Any ideas why it won't work? It's bound to be something obvious....

Cheers

---

### Post by arrange on 2010-06-10
If you do a simple```
* * * * * touch /tmp/test
#

```does it create/update the */tmp/test* file?

---

### Post by ourmartin on 2010-06-10
cheers

Just tried...didn't work
 ??

---

### Post by arrange on 2010-06-10
What does */var/log/syslog* has to say about this? When you change your *crontab* via **crontab -e**, it should be logged there, as well as any jobs that have been run.

For instance```
Jun  8 13:06:15 lucid-lean crontab[21930]: (arrange) BEGIN EDIT (arrange)
Jun  8 13:06:23 lucid-lean crontab[21930]: (arrange) REPLACE (arrange)
Jun  8 13:06:23 lucid-lean crontab[21930]: (arrange) END EDIT (arrange)
Jun  8 13:07:01 lucid-lean cron[826]: (arrange) RELOAD (crontabs/arrange)
Jun  8 13:07:01 lucid-lean CRON[22068]: (arrange) CMD (echo)
Jun  8 13:07:01 lucid-lean CRON[22067]: (arrange) MAIL (mailed 1 byte of output but got status 0x0001#012)
Jun  8 13:08:01 lucid-lean CRON[22228]: (arrange) CMD (echo)
Jun  8 13:08:01 lucid-lean CRON[22226]: (arrange) MAIL (mailed 1 byte of output but got status 0x0001#012)
```

---

### Post by ourmartin on 2010-06-11
Cheers

....i'll get back to you

---

### Post by HermanAB on 2010-06-11
Put the script in /etc/cron.daily

---

