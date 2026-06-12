---
title: "bash set -o vi question"
date: 2010-11-16
forum: General Help
---

### Post by supradave on 2010-11-16
This has been one of my biggest complaints with bash's vi mode.  Back when I used ksh, if you would enter edit mode and edit the command with vi, if it was a multiple line command, the line breaks would appear.  In bash, they don't.  For example:

```
for i in `ls -1`
do
echo $i
done
```

will end up in bash as (Esc - V):

```
for i in `ls -1` do; echo $i; done
```

whereas ksh would put the appropriate line breaks in.

Any idea if getting the line breaks in bash's vi mode is possible?

---

### Post by DaithiF on 2010-11-16
```
shopt -s lithist

```

though the downside is that it makes your history look a little untidy, ie. your history entries will show multi-line commands with newlines (and therefore spread over several screen-lines)

---

