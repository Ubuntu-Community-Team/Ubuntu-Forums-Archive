---
title: "Tricky Sed Regex help"
date: 2010-05-17
forum: General Help
---

### Post by blazemore on 2010-05-17
Hello all,

I'm trying to craft a tricky regex using Sed.
I'm trying to clean up some code which has bazillions of lines over 80 characters in length, mainly because of these end-of-line comments.
I want to change them to a nicer format.

I've put the code on Pastebin because the formatting is better:
[http://pastebin.com/0rcdupjh](http://pastebin.com/0rcdupjh)

Can anyone help me do that? Bear in mind those are tabs, not spaces.

---

### Post by DaithiF on 2010-05-17
Hi, something like:
```
sed -r 's#^(\s*)("[^"]*",)\s*(/\*.*\*/)\s*$#\1\3\n\1\2#' somefile
```

---

