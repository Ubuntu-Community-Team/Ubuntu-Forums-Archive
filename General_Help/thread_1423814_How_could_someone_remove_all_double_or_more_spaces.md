---
title: "How could someone remove all double or more spaces from a group of words?"
date: 2010-03-07
forum: General Help
---

### Post by Rytron on 2010-03-07
Hi.
How could someone remove all double or more spaces from a group of words?
Is there a GUI program or CLI method or both?
Example:
I like to turn this:
```
[COLOR="DarkSlateBlue"]The  quick brown   fox.[/COLOR]
```
into this:
```
**[COLOR="DarkSlateGray"]The quick brown fox.[/COLOR]**
```

---

### Post by howlingmadhowie on 2010-03-07
```

howlingmadhowie% echo "the   quick   brown     fox" | sed -e 's/ \{1,\}/ /g'
the quick brown fox

```

---

### Post by Rytron on 2010-03-07
Thank you howlingmadhowie. :p

---

