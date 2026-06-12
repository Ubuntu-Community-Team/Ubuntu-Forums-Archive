---
title: "GREP - Return only search string"
date: 2011-01-13
forum: General Help
---

### Post by Koffie24 on 2011-01-13
Hi there,

I have a mail.log file, of which I want to redirect only the search strings of the sender from=<example.sender@exampledomain.com> and the size size=4537 to a file.

In every case the sender string starts as from=<> and the size string starts as size=

What would be the grep command to redirect only the two search strings to a .txt file?

---

### Post by DaithiF on 2011-01-13
assuming both occur on the same line, and that the from comes first, then a combination of grep and sed, something like:

```
grep "from=<" somefile | sed 's/^.*from=<\(.*\)>.*size=\([0-9]\+\).*$/\1 \2/' 

```

redirect output to a file to save results once happy its doing what you need.

---

### Post by Koffie24 on 2011-01-14
Thanks DaithiF,

Turns out a regular grep 'somename' was sufficient.

However thanks for the command, helps with the learning process!

---

