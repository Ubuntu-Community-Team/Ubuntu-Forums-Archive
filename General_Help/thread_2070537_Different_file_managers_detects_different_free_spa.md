---
title: "Different file managers detects different free space sizes?"
date: 2012-10-13
forum: General Help
---

### Post by argonvegell on 2012-10-13
I've only been using Xubuntu for about a month now, and I've noticed from discrepancies between Thunar and PCManFM, Thunar records my current free space as 10.8GB, while PCManFM as 11.6GB.  The reason why I have two file managers is that I had to install PCManFM to change some file and folder permissions, PCManFM is easier to use than Nautilus.  Why is Thunar and PCManFM detecting different free spaces?

---

### Post by Wim Sturkenboom on 2012-10-13
With a small difference like this, it might be rounding. PCManFM might round filesizes before adding them to the total; e.g. a 900kB file might be rounded to 1MB.

PS
I only trust commandline tools ;)
```

sudo du -h --max-depth=1 /

```
and
```

df -h

```

---

### Post by Cheesemill on 2012-10-13
Probably one is measuring in GB and the other is measuring in GiB.

---

