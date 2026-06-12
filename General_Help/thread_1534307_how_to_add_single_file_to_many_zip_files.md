---
title: "how to add single file to many zip files?"
date: 2010-07-19
forum: General Help
---

### Post by m666 on 2010-07-19
I have a folder containing 5000+ zip files and I need to add a single file to each zip. How to do it quick way?

---

### Post by gmargo on 2010-07-19
```

find . -type f -name '*.zip' -exec zip -u {} filename_to_add \;

```Test on a subset first!

---

