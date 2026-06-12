---
title: "heirloom-mailx in 12.04 broke my ability to add headers"
date: 2012-08-06
forum: General Help
---

### Post by tbharber on 2012-08-06
Hey all need some help!

So I just upgraded from 11.04 to 12.04.  In the old version I was able to use the command:

```
cat $TEMP | mail -a "Content-type: text/html" -s "Weekly Stat report for $DATE" example@gmail.com
```

This would send an HTML email to my email address with some information.  The problem is with 12.04 it was upgraded to heirloom-mailx, and from what I can gather from Googleing around does not have the ability to use the "-a" flag to specify a content type.  In my example I am unable to make it an HTML email.  This means when I get the email all I see is HTML code.

Does anyone have a workaround or fix for this?  I am willing to roll back to the old mail version if possible but am not sure how.

Any thoughts???

---

### Post by tbharber on 2012-08-08
Still having this issue.  Anyone have any thoughts on this?

---

### Post by mblythe on 2012-09-17
Looks like Uubntu switched from bsd-mailx to heirloom-mailx.  These 2 programs have different command line options, so they are not drop-in replacements for one another (lame!)

[http://man.he.net/man1/bsd-mailx](http://man.he.net/man1/bsd-mailx)

[http://heirloom.sourceforge.net/mailx/mailx.1.html](http://heirloom.sourceforge.net/mailx/mailx.1.html)

It looks like bsd-mailx is still in the ubuntu repositories, so I'd install it, then update your script to specifically point to /usr/bin/bsd-mailx (or wherever it gets installed).

---

