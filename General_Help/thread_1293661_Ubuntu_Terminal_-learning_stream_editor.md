---
title: "Ubuntu Terminal -learning stream editor"
date: 2009-10-17
forum: General Help
---

### Post by dandeliondream on 2009-10-17
Hi I have a data5.txt which contains

happy.ha
mango.g
water.h
tea.h
rolling.s

I'll telling to change anything with .h to 1

In Ubuntu terminal, according to my lecture note...i've tried below line but in vain.
sed 's/<\(.*\).h>/<\1>/' data5.txt

---

### Post by SPr on 2009-10-17
```

sed 's/\.h/1/' data5.txt
happy1a
mango.g
water1
tea1
rolling.s

```
or
```

sed 's/\.h/\.1/' data5.txt
happy.1a
mango.g
water.1
tea.1
rolling.s

```
or
```

sed 's/\.h$/\.1/' data5.txt
happy.ha
mango.g
water.1
tea.1
rolling.s

```
You don't say exactly what you want.
This sounds like homework but I answered because I think it will demonstrate why you need to check your notes for accuracy.

---

### Post by dandeliondream on 2009-10-17
> **SPr said:**
> ```

sed 's/\.h/1/' data5.txt
happy1a
mango.g
water1
tea1
rolling.s

```or
```

sed 's/\.h/\.1/' data5.txt
happy.1a
mango.g
water.1
tea.1
rolling.s

```or
```

sed 's/\.h$/\.1/' data5.txt
happy.ha
mango.g
water.1
tea.1
rolling.s

```You don't say exactly what you want.
This sounds like homework but I answered because I think it will demonstrate why you need to check your notes for accuracy.

:KS Thanks, this helps me to understand better.

---

