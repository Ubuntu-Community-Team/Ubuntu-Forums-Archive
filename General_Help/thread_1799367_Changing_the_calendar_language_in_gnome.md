---
title: "Changing the calendar language in gnome"
date: 2011-07-07
forum: General Help
---

### Post by User-007 on 2011-07-07
Hi all,

I have an English installation of Ubuntu (10.04), but locales are Finnish since I live in Finland. I had a problem that the week started on Sunday but I found some tips from googling. So what I did:

I installed language_support_fi package.

I added a row to /etc/environment 
```
LC_TIME="fi_FI.UTF-8"
```

I ran a command
```
sudo locale-gen
```

OK, this changed the start-of-week-day to Monday. But, now the system language is English but the calendar language is Finnish. Is there any way to change the calendar language back to English but leave the start-of-week-day on Monday?

Any suggestions will be appreciated.

User JB

---

