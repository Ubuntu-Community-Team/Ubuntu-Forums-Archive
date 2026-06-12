---
title: "Subtract two variables in awk"
date: 2011-02-11
forum: General Help
---

### Post by Sam1994 on 2011-02-11
Hey,

Turns out I don't have bc in my Ubuntu distro and I can't install it. Can someone help me subtract two variables (BASH variables) from awk and set the result as another variable, e.g:

finalvalue=`awk '{print $first - $second}'`

Thanks in advance

---

### Post by quadproc on 2011-02-11
How about using dc instead?  It is part of the usual distribution.

quadproc

---

### Post by sisco311 on 2011-02-11
Integer:
```

let final="first - second"
final=$(( first - second ))
(( final = first - second ))

```

Floating point:
```
final=$(echo "$first - $second" | bc)
final=$(echo "$first $second - p" | dc)
final=$(awk -v v1=$first -v v2=$second 'BEGIN {print v1-v2}')
final=$(awk -v v1=$first -v v2=$second 'BEGIN {printf "%.3f\n", v1-v2}')
``` 

See:
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)
and
[http://mywiki.wooledge.org/BashFAQ/022](http://mywiki.wooledge.org/BashFAQ/022)

---

