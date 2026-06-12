---
title: "Date Week of Year"
date: 2012-02-27
forum: General Help
---

### Post by hwttdz on 2012-02-27
Ok, so I need the week of the year for a script (weird right?). And the man page for the date command started my search, and I found:

```
       %U     week number of year, with Sunday as first day of week (00..53)
       %V     ISO week number, with Monday as first day of week (01..53)
       %W     week number of year, with Monday as first day of week (00..53)
```

So, I looked at that, and I figured maybe two of them made sense to me.  I know what Sunday is, and I know what Monday is, and I know what a week is, so this is a good start.  An ISO week is beyond me.  So experimentation to the rescue:

```
for i in {1..366}; do date +"%U %V %W" --date="now + $i day" >> temp.txt; done
```

So I fill temp.txt with all the possible different combinations of week numbers that can occur, and then "uniq temp.txt" will sparse that list out a little.  

Looking at that output I found something interesting:
```
10 10 10
11 11 11
```

All columns change numbers at the same time when Monday and Sunday fall on the same day of the week?  Whaaa?  I'm officially more confused than before.

Not that it's really going to matter for this script, but now I'm curious. Anyone have any ideas?

---

### Post by jacob.david on 2012-02-28
I ran your script and printed the output and everything seems to be normal. Following is the output with uniq -c.

```

4 09 09 09
1 10 09 09
6 10 10 10
1 11 10 10
6 11 11 11
1 12 11 11
6 12 12 12
1 13 12 12
6 13 13 13
1 14 13 13

```

---

