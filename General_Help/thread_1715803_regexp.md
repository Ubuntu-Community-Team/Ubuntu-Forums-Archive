---
title: "regexp"
date: 2011-03-27
forum: General Help
---

### Post by pizet on 2011-03-27
How can I write a regexp so that it matches a string only if it contains and odd number of one character.

For example I want to match 'a' odd times behind itself (a, aaa, aaaaa, aaaaaaa, ...).

I used
```

egrep 'a(aa)*'
```

Why it does not work and it also matches aa, aaaa, aaaaaa, ... ?

---

### Post by d3v1150m471c on 2011-03-27
let me see what i can come up with

---

### Post by amauk on 2011-03-27
put start and end anchors on the regex
Ie.```
egrep '[COLOR="Red"]^[/COLOR]a(aa)*[COLOR="Red"]$[/COLOR]'
```

---

### Post by deconstrained on 2011-03-27
This is obviously a homework problem. Why did you people help him?

---

### Post by amauk on 2011-03-27
> **deconstrained said:**
> This is obviously a homework problem. Why did you people help him?whoops, oh well
It's so long since I've been a student it never even crossed my mind

---

### Post by d3v1150m471c on 2011-03-27
i have no idea how to do it with grep but here's the hard way:
```

#!/bin/bash

var="ababa abababa aba abaaaba"
foo=($var)
for a in ${foo[@]}; do
 c="0"
 b="$a"
 while [[ $b == *a* ]]; do
  b=${b/a/}
  c=$(($c + 1))
 done
 [[ $c == *1 ]] && echo $a
 [[ $c == *3 ]] && echo $a
 [[ $c == *5 ]] && echo $a
 [[ $c == *7 ]] && echo $a
 [[ $c == *9 ]] && echo $a
done

```

---

### Post by pizet on 2011-03-27
I have realized that I have to add the '^' and '$', but thaks anyway to all.

But a homework???

Anyway I just forgot how egrep works.

---

### Post by deconstrained on 2011-03-28
It's just too often that people are doing homework and too lazy to figure it out themselves and post their question on the forum. The post looked suspicious, so I suspected homework, that's all.

Also, in posix-egrep you can use '\b' as an anchor (matches beginning OR end of a string of alphanumerics/underscores). Would work for aaa or aaaaa but not baaac

---

