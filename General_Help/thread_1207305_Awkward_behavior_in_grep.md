---
title: "Awkward behavior in grep"
date: 2009-07-08
forum: General Help
---

### Post by Lucky. on 2009-07-08
So the other night I was trying to find the process name for my DNS server.  I figured I'd start with the following:

```

ps -A | grep dns*

```

Darn, got nothing back.  So then I tried something a litle more simple:

```

ps -A | grep dn*

```

This brought back a slew of items...a few as an example:

```

    2 ?        00:00:00 kthreadd
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    9 ?        00:00:00 kintegrityd/0
   10 ?        00:00:00 kblockd/0
   11 ?        00:00:00 kacpid
   16 ?        00:00:00 ksuspend_usbd
   17 ?        00:00:00 khubd
   18 ?        00:00:00 kseriod
   19 ?        00:00:00 kmmcd

```

Err, not a single one of those have a "dn" in them.  Same results with "da*", "db*", etc.  With three characters and a wildcard, the results appear accurate.  With two characters and a wildcard....not so much.

Am I missing something here, or is this a bug?

---

### Post by sisco311 on 2009-07-08
nothing wrong with the [regular expression]("http://en.wikipedia.org/wiki/Regular_expression")

* - Matches the preceding element **zero** or more times. For example, ab*c matches "ac", "abc", "abbbc", etc. [xyz]* matches "", "x", "y", "z", "zx", "zyx", "xyzzy", and so on. \(ab\)* matches "", "ab", "abab", "ababab", and so on.

---

### Post by mobilediesel on 2009-07-08
> **Lucky. said:**
> So the other night I was trying to find the process name for my DNS server.  I figured I'd start with the following:

```

ps -A | grep dns*

```

Darn, got nothing back.  So then I tried something a litle more simple:

```

ps -A | grep dn*

```

This brought back a slew of items...a few as an example:

```

    2 ?        00:00:00 kthreadd
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    9 ?        00:00:00 kintegrityd/0
   10 ?        00:00:00 kblockd/0
   11 ?        00:00:00 kacpid
   16 ?        00:00:00 ksuspend_usbd
   17 ?        00:00:00 khubd
   18 ?        00:00:00 kseriod
   19 ?        00:00:00 kmmcd

```

Err, not a single one of those have a "dn" in them.  Same results with "da*", "db*", etc.  With three characters and a wildcard, the results appear accurate.  With two characters and a wildcard....not so much.

Am I missing something here, or is this a bug?

Just missing a dot:```
ps -A | grep dns.*
```
the dot stands for "any character" and the star stands for "zero or more of the previous character." Your second example was looking for anything with "d and 0 or more s"

---

### Post by Lucky. on 2009-07-08
Ahh, there's the ticket.  Right on, thanks guys.

---

