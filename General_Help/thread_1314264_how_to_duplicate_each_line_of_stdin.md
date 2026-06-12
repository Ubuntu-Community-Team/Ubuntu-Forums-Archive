---
title: "how to duplicate each line of stdin"
date: 2009-11-04
forum: General Help
---

### Post by cthlhu1987 on 2009-11-04
How to duplicate the stdin like this:
before:
```
foo
bar
baz
quz

```
after:
```
foofoo
barbar
bazbaz
quzquz

```

---

### Post by diesch on 2009-11-04
sed -res'/(.*)/\1\1/'

---

### Post by Giblet5 on 2009-11-04
```
awk '{ printf("%s%s\n", $1, $1); }'
```

---

### Post by diesch on 2009-11-04
awk -F\$ '{print $1$1}'

---

### Post by Giblet5 on 2009-11-04
```
cat > foofoo.c << !
#include <stdio.h>
#include <string.h>

int main()
{
  char bp[1024];
  while(fgets(bp, 1023, stdin)) {
    while(bp[strlen(bp)-1] == '\n') bp[strlen(bp)-1] = '\0';
    if(!strlen(bp)) break;
    printf("%s%s\n", bp, bp);
  }
  return 0;
}
!
gcc -o foofoo foofoo.c
./foofoo
```

---

### Post by cthlhu1987 on 2009-11-04
> **diesch said:**
> sed -res'/(.*)/\1\1/'
> **Giblet5 said:**
> ```
awk '{ printf("%s%s\n", $1, $1); }'
```
> **diesch said:**
> awk -F\$ '{print $1$1}'
Thx, all 3 variants worked. You rule :popcorn::KS:P:D

---

### Post by leandromartinez98 on 2009-11-04
If it was for general file/table editing, you could use vim:

[http://www.youtube.com/watch?v=lFUE7BTUHuc](http://www.youtube.com/watch?v=lFUE7BTUHuc)

Control-V to select
y  to copy
p  to paste

---

