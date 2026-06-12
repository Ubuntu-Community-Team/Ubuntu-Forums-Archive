---
title: "Wildcard in sed&amp;grep that includes line endings?"
date: 2010-12-21
forum: General Help
---

### Post by valros on 2010-12-21
Here's my current regular expression(used in sed):

sed 's/\/\/!Start.*\/\/!End//g' in > out

The only problem being that the wildcard . does not work across multiple lines, [.\n]* doesn't seem to work either.

---

### Post by valros on 2010-12-21
Hm, the -n argument supposedly works to have sed look at multiple lines, although with that option enabled there is no output.

---

