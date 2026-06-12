---
title: "text parsing: remove everything in a line after &quot;: &quot;?"
date: 2012-07-08
forum: General Help
---

### Post by earthpigg on 2012-07-08
(I know it sounds homeworkey, but it isn't... bunch of us on a non-technical hobbyist website are constantly adding words to our little firefox dictionaries, attempting to use this to do it [all at once]("http://cavemonkey50.com/2007/03/edit-firefoxs-spelling-dictionary/") (<-- link) by stripping extraneous information from an existing online dictionary that includes definitions.)

Given a plain text "dictionary" that is formatted as follows:

```
term: definition.
another term: another definition.
and yet another term: and lo, another definition.
```

What would be the most efficient way to strip off everything but the terms themselves? I'm thinking the algorithm, in English, would be "identify and remove everything from the : (inclusive) to the end of line (non-inclusive)."

EDIT: Replace "most efficient" with "least time consuming". I'd be happy to copy/paste/compile some c or python code, but digging up the old "intro to programming" C++ textbook and spending five hours on a self-imposed assignment to recreate what has probably already been created ten thousand times seems unnecessary. :)

---

### Post by earthpigg on 2012-07-08
Solved using these two things as references:

[http://www.oooninja.com/2008/01/text-columns-calc-convert-openoffice.html](http://www.oooninja.com/2008/01/text-columns-calc-convert-openoffice.html)
[http://www.freesoftwaremagazine.com/articles/new_line_search_replace_openoffice_org_writer_lazy_way](http://www.freesoftwaremagazine.com/articles/new_line_search_replace_openoffice_org_writer_lazy_way)

---

### Post by steeldriver on 2012-07-08
... fwiw if you *did* want to do it programatically, there'd be no need to resort to anything as low-level as C - for example you could do it with a simple sed command

```
sed 's/:.*$//' *oldfile* > *newfile*
```

or if you want to do it in place (edit the original file directly)

```
sed -i 's/:.*$//' *file*
```

---

