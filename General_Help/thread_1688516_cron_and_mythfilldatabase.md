---
title: "cron and mythfilldatabase"
date: 2011-02-15
forum: General Help
---

### Post by rbtprkr on 2011-02-15
in a terminal: crontab -e
the first time I ran it it said no crontab for **** (**** being my username). nano opens, I entered: 15 16 * * * mythfilldatabase then yes to save but I am getting stuck on where to save this file the filename shown is: /tmp/crontab.VHaCea/crontab is this right?

---

### Post by DaithiF on 2011-02-15
you don't need to worry about where it is saved -- crontab takes care of that for you.

the file you see in tmp is just a temporary staging file from which crontab takes the content and saves it to the final destination.

that final destination is not important, you never need to edit it other than through crontab.  if curious, the location is  /var/spool/cron/crontabs/youruser

---

### Post by mr_luksom on 2011-02-16
Do you even need a cron job for mythfilldatabase?

I've never set one up, my database updates all the time.

---

### Post by rbtprkr on 2011-02-22
Thank You Daithif
if anybody needs it, the command portion on my original post was wrong  i changed it to:
15 16 * * * /usr/bin/mythfilldatabase
and it's working now

---

