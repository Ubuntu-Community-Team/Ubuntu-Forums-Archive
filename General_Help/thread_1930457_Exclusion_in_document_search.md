---
title: "Exclusion in document search"
date: 2012-02-23
forum: General Help
---

### Post by salmontres on 2012-02-23
Hi guys,

I'm trying to search in my documents for a space character that isn't preceded by a comma. (That is, I want to search " " but that's not ", ".) I know, this is very specific, but, does grep or gedit offer this? (I'm not particular about the editor, I'd just like to know if this can be done.)

---

### Post by erind on 2012-02-23
Try this regex that uses the negative lookbehind: 

```
(?<!,) +
```The regex can be used from the command line - perl, python, etc or easier with gedit with **advanced-find** plugin enabled, which needs some little practice to learn.

[http://code.google.com/p/advanced-find/wiki/Installation](http://code.google.com/p/advanced-find/wiki/Installation)

P.S. The option '*regular expression*' must be checked in *advanced-find* UI when using it.

---

### Post by salmontres on 2012-02-24
Thank you for the quick reply, erind. I'll look into this now.

---

