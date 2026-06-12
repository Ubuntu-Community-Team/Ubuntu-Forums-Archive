---
title: "Panel clock's calendar disagrees with Evolution"
date: 2009-12-16
forum: General Help
---

### Post by Ubunthree on 2009-12-16
I have an event in Evolution's calendar which recurs every two weeks on Friday. However, the panel clock's calendar, which as I understand gets its data from Evolution, shows this event recurring every two weeks on Thursday instead. Any thoughts on why this is? (Karmic, Evolution 2.28.1)

[IMG]http://ubuntuforums.org/picture.php?albumid=1465&pictureid=5349[/IMG]

---

### Post by Ubunthree on 2009-12-18
Deleting the bugged event and recreating it seems to have set it right, though I am still interested in why this happened, to know whether it is worthy of a bug report or not.

---

### Post by Ubunthree on 2009-12-31
No, it's back again:

[IMG]http://ubuntuforums.org/picture.php?albumid=1465&pictureid=5442[/IMG]

The other bolded dates, a recurring monthly event on the 9th and a one-time event on the 29th, are on the correct days. The biweekly PayDay event keeps shifting for some reason.

---

### Post by dcstar on 2009-12-31
Unless you have the timezone in Evolution set to the same timezone in your install then there will be a discrepancy.

```
man tzselect
```

---

### Post by Ubunthree on 2009-12-31
I have "Use system time zone" checked in the Calendar preferences, and it shows the correct tz being used. I hadn't thought to look at this, so it was a good suggestion, but it doesn't seem to be the cause.

Thanks anyway!

---

