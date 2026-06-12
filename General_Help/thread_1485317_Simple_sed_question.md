---
title: "Simple sed question"
date: 2010-05-16
forum: General Help
---

### Post by e64462 on 2010-05-16
I've been searching for a while now, but everything I've found wants to do the exact opposite of what I need.

I'm looking to replace all newlines in a file with the actual '\n' string.

So, for example. If my file contained:
> one
two
three
I would like the output after i type the command to be
> one\ntwo\nthree

Most of the help I've found is to do the exact opposite. I've tried tr and sed, but I'm not abundantly familiar with regex does anyone have a suggestion?

---

### Post by e64462 on 2010-05-16
If anyone ever navigates to this page with a similar problem, the solution I found is:

> sed -e :a -e ';$!N;s/\n/\\n/;ta' file

---

### Post by DaithiF on 2010-05-17
Hi,
you could simplify that sed expression a little:
```
sed -e :a -e 'N;s/\n/\\n/;ta' file 
```

and another way, using sed and tr in combination, (and possibly slightly less baffling to people not very familiar with sed since it avoids the need for the 'advanced' N operator) would be:
```
sed 's/$/\\n/' testfile | tr -d '\n'
```
(ie. first use sed to add the '\n' characters to the end of each line, then use tr to delete the actual newlines.

---

