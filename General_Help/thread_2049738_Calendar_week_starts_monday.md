---
title: "Calendar week starts monday"
date: 2012-08-29
forum: General Help
---

### Post by neur0 on 2012-08-29
Hello,

I can't seem to fix the issue I am having with changing the starting day from Sunday to Monday in the calendar (tested with Orage and cal).

I tried changing my "/usr/share/i18n/locales/en_US" every way I could think of. 
Currently the relevant portion of the file looks like this:

```

week    7;19971130;4
first_weekday   2
first_workday   2

```

Any suggestions ?

---

### Post by Pand5461 on 2012-08-29
cal -m displays a calendar with Monday as the first day.

To change it system-wide: [https://wiki.archlinux.org/index.php/Locale#Setting_the_first_day_of_the_week](https://wiki.archlinux.org/index.php/Locale#Setting_the_first_day_of_the_week)

---

### Post by neur0 on 2012-08-29
Thanks for the reply.

Looks like the -M switch works only with ncal, but regardless, the main problem is with Orage. I use cal only as a test tool.

I tried the values suggested in the link but none of the changes have an effect on the calendar.
My "locale" output says I use en_US.UTF-8 for everything including LC_TIME so I would expect that calendar would change after editing the file noted in the first post and doing "locale-gen" and restarting X. However, nothing changes.

---

### Post by Pand5461 on 2012-08-29
Is it critical for you to use en_US locale? I remember I had week starting from Monday with en_GB.

---

### Post by neur0 on 2012-08-30
Ok, I want to try that, but how do I change the locale?

I followed some online documentation, but nothing works.

My /etc/default/locale now looks like this:
```

LANG=en_GB.UTF-8
LC_MESSAGES=POSIX

```

And after reboot "locale" command says everything is stil en_US.UTF-8

Any Ideas ?


EDIT: I managed to change most of the settings in XFCE's GUI settings tool "Language Support"
It looks like XFCE has it's own locale setting hidden somewhere.
This made Orage display Monday as the first weekday, but "cal" output is still unchanged. I needed Orage set up so I'll mark it solved.
Thanks for the help

---

### Post by aikikode on 2012-09-23
> **neur0 said:**
> Hello,

I can't seem to fix the issue I am having with changing the starting day from Sunday to Monday in the calendar (tested with Orage and cal).

I tried changing my "/usr/share/i18n/locales/en_US" every way I could think of. 
Currently the relevant portion of the file looks like this:

```

week    7;19971130;4
first_weekday   2
first_workday   2

```Any suggestions ?

You need to call:
```

# locale-gen
```and reboot then.

---

