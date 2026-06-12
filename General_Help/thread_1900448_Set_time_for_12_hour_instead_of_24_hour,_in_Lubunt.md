---
title: "Set time for 12 hour instead of 24 hour, in Lubuntu?"
date: 2011-12-26
forum: General Help
---

### Post by pretty_whistle on 2011-12-26
The clock panel applet is set for the 24 hour but I want to set it for 12 hour.  I can't stand it when I want to know what time it is and it shows 1300 (or whatever) instead of 1pm, so I have to sit there and count to figure out what time it is.

Is it possible to change the clock to display 12 hour am/pm time?

---

### Post by TeoBigusGeekus on 2011-12-26
Right click it->Edit Digital Clock settings.
Change clock format from %R to %r.

---

### Post by guestolo on 2011-12-26
Can you right click on the clock and select Digital Clock Settings
Under Clock Format
Change to something like

```
%a %b %I:%M %P
```That will give you Date/day time

You can change that to your own preference
More info in terminal type in
**man strftime**

---

### Post by pretty_whistle on 2011-12-26
> **TeoBigusGeekus said:**
> Right click it->Edit Digital Clock settings.
Change clock format from %R to %r.
No kidding?  That easy?  Cool.

Thanx.

That resolved it.

---

### Post by Butthead on 2011-12-26
You can always change how time is displayed by choosing "System Settings - Regional & Language - Time & Dates (Tab)" and changing how it's displayed in there too. =;

---

### Post by Gray Beard on 2012-04-28
Right click on the LXDE panel's digital clock and then left click on "Digital Clock" Settings. The configuration window that pops up will refer you to man 3 strftime. That function was not present in 11.04 but it was present in 11.10. In 12.04, it's gone again. In 11.04, I couldn't figure out why the manual page was missing but this time around, I got lucky. The answer was at

[http://kernel.org/doc/man-pages/missing_pages.html](http://kernel.org/doc/man-pages/missing_pages.html)

In short, crank up Synaptic and add two packages:
manpages-posix and manpages-posix-dev.

As always, thanks to those who share their knowledge.

---

### Post by sheridanm962 on 2012-05-14
Just to let anyone know how to actually change it in most recent distros add in this: ```
%I:%M:%S %p
```

Replace the %R part with the code.

enjoy.

Oh and for the record I use Ubuntu with LXDE, Compiz has better performance with it.

---

### Post by walidzohair on 2013-01-06
> **TeoBigusGeekus said:**
> Right click it->Edit Digital Clock settings.
Change clock format from %R to %r.

Thanks worked like a charm.

I hd to re-set my password using my old dell inspiron 6000 with keybordtht have the a, . not working specially to reply to you and thank you..

and hey guys with old machines looking for something lighter than even xp do not think of windows 7 or 8 .... just go LUBUNtu!!! ;)

:D

---

### Post by trh51 on 2013-03-11
Works great! Thanks for the tip!

---

### Post by philpense on 2013-05-16
Followed the guidance of this post reply.  The format is now 12hr but four hours ahead of the correct time.  BIOS time was correct when last checked.  Guidance sought.

---

### Post by Impavidus on 2013-05-16
Then you have a problem with your time zone settings. Check them and, if dual booting with windows, check the time zone settings and clock there too. Furthermore, as your problem has nothing to do with the original question and this is an old thread, I advise you to start a new thread if this doesn't solve the problem.

---

