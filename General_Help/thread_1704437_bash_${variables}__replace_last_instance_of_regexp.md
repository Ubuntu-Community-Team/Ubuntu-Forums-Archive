---
title: "bash ${variables} : replace last instance of regexp"
date: 2011-03-10
forum: General Help
---

### Post by d3v1150m471c on 2011-03-10
I have something like...
```

var=beer
# echo ${var/%e/E} doesn't do anything because i can only replace "r" or "er" this way
# and I have A LOT of variables to work with so i can't make individual exceptions to each #one

# so... how could i replace the last instance of a regexp in each variable?

```

:D thanks in advance.

---

### Post by TeoBigusGeekus on 2011-03-11
If I understand correctly, you want to replace the last 'e' that sed finds:
```
var=beer
echo $var|sed 's/\(.*\)e/\1E/'
```

---

