---
title: "unity panel clock question"
date: 2010-10-12
forum: General Help
---

### Post by Zlatan on 2010-10-12
hello, how  can i change ubuntu unity 12hr clock to 24hr clock? thank you

---

### Post by schelf on 2010-10-13
Well, it seems you can't :confused:
I tried but I see no options in the Time & Date settings.
When I switched my language to Dutch it appeard in 24h format, switching back to Englisch and it is back to 12h.
Does that count as a bug?

---

### Post by Zlatan on 2010-10-13
> **schelf said:**
> Well, it seems you can't :confused:
I tried but I see no options in the Time & Date settings.
When I switched my language to Dutch it appeard in 24h format, switching back to Englisch and it is back to 12h.
Does that count as a bug?

oh i'm not a developer but i think it will be a temporary limitation for the first version of unity related to your language/locale selection...

---

### Post by nardusg on 2010-10-21
[http://www.omgubuntu.co.uk/2010/09/enable-date-day-seconds-on-indicator-datetime/](http://www.omgubuntu.co.uk/2010/09/enable-date-day-seconds-on-indicator-datetime/)

---

### Post by Zlatan on 2010-10-22
> **nardusg said:**
> [http://www.omgubuntu.co.uk/2010/09/enable-date-day-seconds-on-indicator-datetime/](http://www.omgubuntu.co.uk/2010/09/enable-date-day-seconds-on-indicator-datetime/)

! thanks mate

---

### Post by stoian on 2012-08-06
or, you can do that directly from the command-line:

```
gsettings set com.canonical.indicator.datetime time-format custom && gsettings set com.canonical.indicator.datetime custom-time-format "%A, %B %e, %H:%M"
```

the symbols/parameters for setting the date-time format can be found by this help for date command:

```
date --help
```

---

### Post by wildmanne39 on 2012-08-06
Thanks for sharing. Thread Closed.

---

