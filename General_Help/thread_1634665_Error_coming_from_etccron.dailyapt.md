---
title: "Error coming from: /etc/cron.daily/apt"
date: 2010-11-30
forum: General Help
---

### Post by shadow_code on 2010-11-30
Hi, since I setup my system so that I'd receive system errors via email, I get an email each day from /etc/cron.daily/apt.

Just wondering why this is, how I can fix it, or if I can just remove apt from cron.daily?

> To: root@jon-desktop
Subject: fcron <systab@jon-desktop> run-parts --report /etc/cron.daily

/etc/cron.daily/apt:
No protocol specified

cheers, Jon

---

### Post by dcstar on 2010-12-01
> **shadow_code said:**
> Hi, since I setup my system so that I'd receive system errors via email, I get an email each day from /etc/cron.daily/apt.

Just wondering why this is, how I can fix it, or if I can just remove apt from cron.daily?



cheers, Jon

[LIST=1]
[*]Do not quote data.
[*]That seems to indicate a problem with APT, you should look at fixing it as it is important to do the regular update checks.
[/LIST]

---

### Post by shadow_code on 2010-12-05
I've managed to narrow it down to update-apt-xapian-index which produces the following error when run in /etc/cron.daily/apt

```
No protocol specified
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
 warnings.warn(str(e), _gtk.Warning)
The index /var/lib/apt-xapian-index is up to date
```

It looks like it's trying to show a warning but the DISPLAY env isn't set for cron tasks.

Any ideas?
cheers

---

### Post by shadow_code on 2010-12-05
Also getting an error from the weekly job:

```
Subject: fcron <systab@jon-desktop> run-parts --report /etc/cron.weekly

/etc/cron.weekly/apt-xapian-index:
No protocol specified
```

---

