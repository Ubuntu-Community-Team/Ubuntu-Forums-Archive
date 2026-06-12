---
title: "How can I find out how many Firefox bookmarks I have?"
date: 2009-12-06
forum: General Help
---

### Post by Rytron on 2009-12-06
Hi.
Is there a way to find the total number of bookmarks I have in Firefox?

---

### Post by StuartN on 2009-12-06
> **Rytron said:**
> Hi.
Is there a way to find the total number of bookmarks I have in Firefox?

You can get an answer by backing up your bookmarks and counting the number of occurences of "lastModified", which probably occurs once per bookmark. It is possible that this string occurs exactly once per bookmark and nowhere else, but it may apply to non-bookmark entries, such as menu items.

```
grep -o "lastModified" Bookmarks\ 2009-12-01.json | wc
```

---

### Post by Rytron on 2009-12-06
> **StuartN said:**
> You can get an answer by backing up your bookmarks and counting the number of occurences of "lastModified", which probably occurs once per bookmark. It is possible that this string occurs exactly once per bookmark and nowhere else, but it may apply to non-bookmark entries, such as menu items.

```
grep -o "lastModified" Bookmarks\ 2009-12-01.json | wc
```

Smart code.
I ran it and got this:
```
1205    1205   15665
```

Does it mean I have 1205 bookmarks? What does 15665 signify?

---

### Post by audiomick on 2009-12-06
> **Rytron said:**
> Smart code.
I ran it and got this:
```
1205    1205   15665
```

Does it mean I have 1205 bookmarks? What does 15665 signify?

You spend too much time in the net?? ;)

---

### Post by StuartN on 2009-12-07
> **Rytron said:**
> Smart code.
I ran it and got this:
```
1205    1205   15665
```

Does it mean I have 1205 bookmarks? What does 15665 signify?

Yes, the numbers output by wc are lines, words and characters. The output from grep is each occurrence of "lastModified" on a separate line, so word and line counts are the same (and 15665 is exactly 1205 times the length of "lastModified" + 1 linefeed, 13 characters each). You could use wc -w to get just the word count.

(man grep and man wc give very comprehensive information about the options).

---

### Post by Rytron on 2009-12-07
Thank you StuartN. I'm surprised Firefox doesn't have an easy function to show the total number of bookmarks. Perhaps there will be an addon released some time.

Cheers.

:popcorn:

---

### Post by fsieber on 2013-04-09
I found this a little more accurate:

          grep -o "A HREF="  <file spec of html backup of bookmarks from firefox libary page> | wc

---

### Post by oldos2er on 2013-04-09
Closed, please don't bump old threads.

---

