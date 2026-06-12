---
title: "Using wget to save a frequently updated webpage"
date: 2010-03-03
forum: General Help
---

### Post by zorblek on 2010-03-03
I'm trying to figure out how to use wget to save a copy of a page that is frequently updated. Ideally, what I'd like it to do is save a copy of the page every minute or so. I don't need multiple copies; I just need to know what the most recent version was. Also, if the page disappears for whatever reason, I don't want it to save the error page, just wait until the page is up again.

Is this possible? It seems like it should be, but I haven't been able to figure it out.

---

### Post by chomps on 2010-03-03
Hi, I would use wget something like this:

wget -r -nd --delete-after /var/www/yourfile.txt

This is assuming the file is beig hosted in /var/www if not point it to the server url.
I would then go use the crontab file located usually under /etc depending on your distro, and set a time schedule to go carry out this command

---

### Post by zorblek on 2010-03-03
Unfortunately, that winds up automatically deleting the file. If I remove "--delete-after", it retains the file, but saves multiple copies, i.e. index.html, index.html.1, etc., instead of just updating the original copy.

Also, FYI, this isn't on my server (forgot to mention that before).

Cron did work, however.

Ideally what I want it to do is save a complete copy of the webpage (with images, stylesheets, etc.) and not make multiple copies. But so far it seems like I can do one or the other but not both.

---

