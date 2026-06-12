---
title: "what does this message mean?"
date: 2009-11-13
forum: General Help
---

### Post by rifak on 2009-11-13
so i just updated a package 'tzdata' and after the unpacking and configuration, i got this message in the terminal:

```
Unpacking replacement tzdata ...
Setting up tzdata (2009r-0ubuntu9.10) ...

Current default time zone: 'America/New_York'
Local time is now:      Fri Nov 13 12:42:40 EST 2009.
Universal Time is now:  Fri Nov 13 17:42:40 UTC 2009.
Run 'dpkg-reconfigure tzdata' if you wish to change it.
```

i have never seen this before and have no clue what its trying to tell me...any thoughts?

---

### Post by coffeecat on 2009-11-13
From the tzdata package information:

> This package contains data required for the implementation of
standard local time for many representative locations around the
globe. It is updated periodically to reflect changes made by
political bodies to time zone boundaries, UTC offsets, and
daylight-saving rules.

I guess it's just telling you what your present settings are, and is asking if you are happy with them. Are you? :)

---

### Post by wirelessmonkey on 2009-11-13
tzdata is "Time Zone Data", the output you recieved just describes your local timezone and Universal time (Greenwich, I think...), and gives you the method to change that data, i.e. dpkg-reconfigure tzdata

---

### Post by rifak on 2009-11-13
thanks for the info. by the way, wirelessmonkey, your signature is awesome. have you met the atheists nightmare? haha

[http://www.youtube.com/watch?v=7sanplNTr6c](http://www.youtube.com/watch?v=7sanplNTr6c)

---

### Post by wirelessmonkey on 2009-11-16
Yep, I love nonsense as much as anyone, I suppose.

---

