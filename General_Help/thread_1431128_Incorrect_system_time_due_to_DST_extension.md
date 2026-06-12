---
title: "Incorrect system time due to DST extension"
date: 2010-03-16
forum: General Help
---

### Post by rslee on 2010-03-16
Hi, 

I live in Chile.  Due to the recent earthquake, [Daylight Savings Time was extended to April 3rd]("http://www.timeanddate.com/news/time/chile-extends-dst-2010.html"), but my Ubuntu machine set its clock back an hour last weekend, which was when DST was originally set to end.  I manually reset the time, but when I resumed from hibernate the clock was wrong again.  How do I turn off synchronization until April 3rd?  More importantly, who needs to be notified of the change to get the problem fixed?

Thanks!

---

### Post by bluefrog on 2010-03-16
I would say a bug report (even if it's not really a bug in that case, more a change) against tzdata would do.

Now will it be solved before April 3rd is another question.
In my company that would be an emergency change because servers / production may be impacted because of this extension.

---

### Post by rslee on 2010-03-22
Thanks, and how do I go about disabling synchronization until April 3rd?

---

### Post by Cyan_Fire on 2010-03-22
System -> Administration -> Time and Date.

Set configuration to manual.

---

### Post by gmargo on 2010-03-22
The latest time zone database (2010f) was just released today. It includes the Chile time change.  That version is not available from Ubuntu yet.

Two ways to get this update right now:

1. Download the files yourself and compile them (See [http://www.twinsun.com/tz/tz-link.htm](http://www.twinsun.com/tz/tz-link.htm))

2. Download and decompress the attachment.  I compiled the new database, and have attached the single timezone file for the "America/Santiago" timezone.   All you have to do is copy this file to /etc/localtime (make a backup!) and it should work immediately.

```

$ date ; date -u
Mon Mar 22 10:43:32 PDT 2010
Mon Mar 22 17:43:32 UTC 2010

$ gunzip Santiago.tz.gz
$ sudo cp -p /etc/localtime /etc/localtime.00
$ sudo cp -p Santiago.tz /etc/localtime

$ date ; date -u
Mon Mar 22 14:43:43 CLST 2010
Mon Mar 22 17:43:43 UTC 2010

```

---

### Post by rslee on 2010-03-22
Thanks gmargo.

I tried the first option but couldn't download the file so I went off to look for an alternative (forgetting that you suggested a second solution, the file you posted).  I found this:

[http://www.debian-administration.org/article/Updating_your_timezone_data_for_daylight_savings_changes](http://www.debian-administration.org/article/Updating_your_timezone_data_for_daylight_savings_changes).

It worked, with one small modification (changing "feisty" to "karmic" in the repository string).  In retrospect, I would have preferred your second solution, as it's less invasive.  But I thought I'd offer this one as well in case anyone needs it.

Gracias y saludos!

---

