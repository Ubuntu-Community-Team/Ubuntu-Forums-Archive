---
title: "Get man pages with the same name"
date: 2010-04-14
forum: General Help
---

### Post by lavinog on 2010-04-14
I was looking at the init man page using
```
man init
```
I get [noparse]init(8) and there is a reference to init(5).[/noparse]  How do I get [noparse]init(5)?[/noparse]

If I use yelp:
```
yelp man:init
```
I get [noparse]init(5) but not init(8)[/noparse]

---

### Post by hryanjones on 2010-04-14
I forgot how to do this as well, but I looked in 
```
man man
```
and near the top found:

       **man**  [-C  file]  [-d]  [-D]  [--warnings[=warnings]]  [-R encoding] [-L
       locale] [-m system[,...]] [-M path] [-S list]  [-e  extension]  [-i|-I]
       [--regex|--wildcard]   [--names-only]  [-a]  [-u]  [--no-subpages]  [-P
       pager] [-r prompt] [-7] [-E encoding]  [--no-hyphenation]  [-p  string]
       [-t] [-T[device]] [-H[browser]] ["-X"[dpi]] [-Z] **[[section] page ...] ...**

which is a big mess whose parts I've bolded boil down to do this
```
man 5 init
```

>>>man man
will also tell you more about those different sections

Hope that answers it, Cheers!

---

### Post by Lord DEA on 2010-04-14
yes, go with
```

man 5 init

```
should be what you're looking for

---

### Post by lavinog on 2010-04-14
Thank you.
I never knew that the numbers signified different sections.  I thought a section would be within a document...ah but it explains it nicely in man man...[slaps forehead]

---

