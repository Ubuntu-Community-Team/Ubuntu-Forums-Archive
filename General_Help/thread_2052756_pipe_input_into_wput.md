---
title: "pipe input into wput?"
date: 2012-09-03
forum: General Help
---

### Post by Kdar on 2012-09-03
How can I pipe input into wput?

I have tried to use &#8722;&#8722;input&#8722;pipe=command flag, however it didn't work. Maybe I am just doing it wrong.

Initially I tried something like this:

```
gzip -fc fileInput | wput ftp://user:password@serverIP/
```

then I tried this:

```
wput --input-pipe="gzip -fc fileInput" ftp://user:password@serverIP/
```

But this doesn't work as well.

---

### Post by Kdar on 2012-09-04
Does anyone have idea?

---

