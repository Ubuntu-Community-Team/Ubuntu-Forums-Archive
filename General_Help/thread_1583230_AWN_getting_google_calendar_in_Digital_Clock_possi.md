---
title: "AWN: getting google calendar in Digital Clock possible?"
date: 2010-09-27
forum: General Help
---

### Post by kpuz on 2010-09-27
In the awn digital clock preferences menu there is a command area which reads 'Run Calendar'. In the following input area I have this command to run the evolution calendar 'evolution calendar:///?startdate=%(year)02d%(month)02d%(day)02dT120000'. Since I don't use evolution I was wondering if there is a command that would allow either the thunderbird calendar or Google calendar to be displayed instead. If anyone has any ideas please share.

---

### Post by sanderd17 on 2010-10-07
If you install prism,

```

sudo aptitude install prism

```

and you create a prism google calendar.

run the prism app, set the url to "http://www.google.com/calendar/", choose the name and extra options if wanted. Create a desktop shortcut to know the command. Right click on that shortcut, choose properties en copy the command to the command in the AWN clock.

This wil always open the calendar at the current date. if anyone has a clue on how to open it on the selected date, please let it know. I can't find anything on the php options needed to navigate to a date.

grtz,
Sander

---

### Post by sssent on 2010-11-21
> **sanderd17 said:**
> 
(...)
This wil always open the calendar at the current date. if anyone has a clue on how to open it on the selected date, please let it know. I can't find anything on the php options needed to navigate to a date.
(...)


You can use the "date" query paratemer with a value YYYYMMDD. I use chromium instead of prism, so my Run calendar command looks like this:
```
/usr/bin/chromium-browser --app="https://www.google.com/calendar/b/0/render?date=%(year)04d%(month)02d%(day)02d"
```

The catch is the clock applet doesn't like "&" characters, so you can't specify more than one query string parameter, only the first will remain in the string. I tried encoding "&" as "%26", but apparently the applet doesn't like "%" characters either (it completely breaks the command).

---

### Post by sanderd17 on 2010-11-21
thanks, that worked good.

---

