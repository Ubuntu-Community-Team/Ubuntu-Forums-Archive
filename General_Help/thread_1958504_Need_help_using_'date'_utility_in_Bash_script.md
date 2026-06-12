---
title: "Need help using 'date' utility in Bash script"
date: 2012-04-14
forum: General Help
---

### Post by Phoenix_Swelter on 2012-04-14
I have a script in which I am attempting to use today's date in my locale, and figure corresponding day of the week in another time zone. In other words, if my time zone is -0400 and the time is 22:00 on Wednesday, I want 'date' to return the fact that it is Thursday in time zone +0100.

This was my attempt:

```
date --date="$(date '+%y-%m-%d %H:%M:%S') +0100" '+%A'
```What actually happened is that 'date' thought it was 22:00 on Wednesday in time zone +0100 and told me it was still Wednesday in my time zone. :mad:

Is there a way to use 'date' for this purpose? Is there another utility out there that would be better for what I'm attempting to do?

---

### Post by Vaphell on 2012-04-14
don't do any math by hand, just run date with different time zone default

```
cd /usr/share/zoneinfo; ls
```

any file located there and in subdirs can be used to set TZ variable right before date command to override the default
just run
```
TZ=GMT date
TZ=EST date
TZ=Europe/London date
```

[http://www.safeer.in/2010/04/converting-time-between-timezones-in.html](http://www.safeer.in/2010/04/converting-time-between-timezones-in.html)

---

### Post by Phoenix_Swelter on 2012-04-14
I had been working that direction. I had been following on this line...

```
TZ=Europe/London
TEST=$(date '+%R %A')
echo $TEST
```

This still returned my local time and day.

But your suggestion finally capped off what I needed:

```
TEST=$(TZ=Europe/London date '+%R %A')
echo $TEST
```

Thank-you.

---

