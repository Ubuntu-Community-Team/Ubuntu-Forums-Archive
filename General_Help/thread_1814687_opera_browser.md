---
title: "opera browser"
date: 2011-07-29
forum: General Help
---

### Post by Matrix01 on 2011-07-29
Opera browser freezed,
I uninstalled it, and reinstalled it,

it freezed again.

---

### Post by mikewhatever on 2011-07-30
Well, I guess reinstalling didn't help.:P

---

### Post by lovinglinux on 2011-07-30
Close Opera, open a terminal, paste the following code and hit Enter:

```
opera -pd ~/.opera-test/
```

If it works, then the problem is in your opera profile. If you need to preserve bookmarks passwords and so on, then you need to figure out which file is causing the problem. I would start removing *operaprefs.ini* from your profile, which is located in the hidden folder *.opera* under your home. If you don't care about your Opera personal data, then simply delete that folder.

---

