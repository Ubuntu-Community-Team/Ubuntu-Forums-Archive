---
title: "How does one use egrep with groups?"
date: 2011-01-17
forum: General Help
---

### Post by Rodayo on 2011-01-17
To put it simply I want the egrep command to return matches for a group rather than the whole pattern itself. 

For example:
```
egrep "real\s([0-9]+?m[0-9]+?\.[0-9]{3}s)" tmp
```

returns 
"real    0m1.001s"

But I want it to return just "0m1.001s", the portion is the group.

If you have an answer could you generalize it for use with multiply groups? Say if I had a group within a group or two groups as part of the whole expression.

I can already guess that I can just apply egrep to whatever the first command returns but is there an easier way to do it?

---

### Post by dysentry on 2011-01-17
You could always pipe it to cut, eg:

```
echo "real 0m1.001s"| cut -f2 -d" "
```

---

### Post by Rodayo on 2011-01-17
> **dysentry said:**
> You could always pipe it to cut, eg:

```
echo "real 0m1.001s"| cut -f2 -d" "
```

Hmm, I appreciate your trying but that's more of a quick fix that applies to this particular example. It wouldn't be applicable if I had many more groupings to match with. Plus I tried it out; the output from cut gives me the same output as before.

Edit: btw, that's a tab char. between "real" and "0m...", not a space. I should've clarified that. It got cut-off when I pasted it...

---

### Post by gmargo on 2011-01-17
```

$ echo "real  0m1.001s" | sed 's/^real[[:space:]]\+//'
0m1.001s

```This sed regex will eat any whitespace whether tabs or spaces.

If you need a more specific answer, then you need to give better examples of your input, and explain or show what you mean by "group within a group or two groups".

---

### Post by sisco311 on 2011-01-17
I would parse the file with awk:
```
awk '{if ($1=="real") print $2} filename
```

---

