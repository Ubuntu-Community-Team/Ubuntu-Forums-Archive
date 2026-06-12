---
title: "Requesting 1 liner regex shell command"
date: 2010-02-11
forum: General Help
---

### Post by chris_l_13 on 2010-02-11
Anyone know of a quick and easy 1 liner to find something like this  in a file:

property=blahblahblah

and change it to:

property=somethingelse

Thanks!

Chris

---

### Post by djurny on 2010-02-11
> **chris_l_13 said:**
> Anyone know of a quick and easy 1 liner to find something like this  in a file:

property=blahblahblah

and change it to:

property=somethingelse

Thanks!

Chris

this will replace all lines with only 'a=blahblahblah' with 'a=somethingelse' in file 'aaa'

```

sed "s|^a=.*$|a=somethingelse|" aaa

```

could also be done with some pattern matching, but this works just as well..

to replace the file 'aaa' itself without redirecting the 'sed' output to another file, use the '-i' option..

---

### Post by hvbakel on 2010-02-11
Here's another one, this will replace all occurrences in the file and keep a copy of the old file with the symbol '~' appended to the filename.

```
perl -pi~ -e 's/property=something/property=somethingelse/g' filename
```

Try googling for 'perl oneliners' and you'll find many other convenient commands.

---

