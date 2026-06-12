---
title: "crontab for changing a html file"
date: 2012-02-16
forum: General Help
---

### Post by gypsumwolf on 2012-02-16
How would I use crontab to have it modify a few lines 
in a existing html file once per week?

I want to have the lines of html removed and then added back on saturdays.

I am not using php or javascript, just plain html.

---

### Post by Lars Noodén on 2012-02-16
One way, using plain HTML, would be to use [server-side includes](https://httpd.apache.org/docs/current/howto/ssi.html).  (Be sure to use [IncludesNOEXEC](https://httpd.apache.org/docs/2.2/mod/core.html#options)) Then you could have the main file point to another file to be inserted.  The cron job could alternately empty and fill that second file.

Otherwise, if you're going to try to mess with the content of the file directly, you're going to want a proper XHTML parser.

---

### Post by Lars Noodén on 2012-02-16
Another option would be to have two versions of the same file and just copy them back and forth using cron.  It's just that when you update one, you have to remember to update the other.

---

### Post by gypsumwolf on 2012-02-16
> **Lars Noodén said:**
> Another option would be to have two versions of the same file and just copy them back and forth using cron.  It's just that when you update one, you have to remember to update the other.

I may endup doing it this way since it would be easiest.

---

