---
title: "Can't Select San Francisco Time Zone"
date: 2006-05-10
forum: General Help
---

### Post by elamericano on 2006-05-10
Do I really have to say I'm in L.A.? You couldn't pay me enough to live there. [-( 

I see Boise, Phoenix, Denver, and Shiprock?! Those are all Mountain Time. Why only one Pacific?

I suppose I can't add San Francisco, and my only option is to pick Vancouver or Tijuana?

---

### Post by 1337hacker on 2006-05-10
its just time man
it doesnt matter what city as long as its the same time zone

---

### Post by elamericano on 2006-05-10
There are US/Pacific and a PST8PDT timezones. Does anyone know where the zone is set manually on a Debian system?

Try to remember, Linux is about choice ;)

---

### Post by elamericano on 2006-05-10
Hey, I was able to add San Francisco to /usr/share/zoneinfo/zone.tab !

When I go to adjust date and time, there's a point for San Francisco now. \\:D/  You can add your hometown too.

I can see there that Shiprock is Navajo territory, which explains why there is a difference in time for that location.

I know this seems useless for some of you, but it is a fun customization. Mac OS has Cupertino, CA as a timezone, so I guess I'm not the only one. :D

---

### Post by elamericano on 2006-05-11
I should mention that if you create something like America/San_Francisco, it should exist in:

/usr/share/zoneinfo/America/San_Francisco
/usr/share/zoneinfo/posix/America/San_Francisco
/usr/share/zoneinfo/right/America/San_Francisco

before you switch zones. You can either copy and rename your zone representative (Los_Angeles in this case) or you can compile it from a modified timezone file from libc6 source. Maybe I'll write a howto ;-)

When you switch zones using Adjust Date & Time, /etc/timezone and /etc/localtime will get updated.

---

