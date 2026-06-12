---
title: "KTader does not find postscri[t part"
date: 2010-08-22
forum: General Help
---

### Post by Colin@oxford on 2010-08-22
I am looking at a program that is attempting to display some PS file and is using KTrader to find a suitable component. The code called is:

```

KTrader::self()->query("application/postscript","'KParts/ReadOnlyPart' in ServiceTypes");

```

This is returning an empty list and so the program reports that it is unable to continue.

What do I need in order for this call to succeed?

---

