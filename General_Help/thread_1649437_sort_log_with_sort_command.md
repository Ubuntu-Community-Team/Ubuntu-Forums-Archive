---
title: "sort log with sort command"
date: 2010-12-20
forum: General Help
---

### Post by narcisgarcia on 2010-12-20
I want to fusion similar logs to a sorted result:
```
cat /var/log/auth.log /var/log/daemon.log | sort ... > analysis.log
```
But I need to get it sorted by date&time, and the date is sorted with a word-month field, and a numeric field, which cannot be sorted alphabetically.
- I need "Nov" to go before "Dec"
- I need the day "2" to go before the day "10"
- I need the time "00:15:01" to go before the time "00:48:02"
- And finally, the rest of the line unsorted.

I've tried with this:
```
cat /var/log/auth.log /var/log/daemon.log | sort -k 3,3r -k 2,2n -k 1,1Mr
```
But the result is not sorted as a single log. I may not be understanding the syntax of "-k" fields.

---

