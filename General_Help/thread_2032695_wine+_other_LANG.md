---
title: "wine+ other LANG"
date: 2012-07-24
forum: General Help
---

### Post by icegood on 2012-07-24
How to make wine to see ANSI cyrillic if kubuntu distro is english.
set | grep LANG:
```

LANG=en_US.UTF-8
LANGUAGE=en_US
    LANG=C LC_MESSAGES=C svn info --non-interactive 2> /dev/null | while read line; do

```

---

