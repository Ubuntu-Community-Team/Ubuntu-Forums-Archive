---
title: "newb needs help with scripting"
date: 2010-11-22
forum: General Help
---

### Post by desreguard on 2010-11-22
Hey guts this is my first ever post on this forum, hoping to find great insights and new ways to discover linux. I have just started scripting with linux and have run into some problems with the syntax or something wondering if anyone can help. sry but im a newb. Here is my code (very simple)

a=1
b=2
c=3
total=a+b+c
echo $total

the echo $total is suppose to print 6 (1+2+3=6), but it just prints a+b+c
I know its probably something small that im over looking but the book that im using is a little outdated so the syntax might have changed or something any help would be very appreciated.

---

### Post by bonixavier on 2010-11-22
[Bash guide for beginners.]("http://tldp.org/LDP/Bash-Beginners-Guide/html/")

---

### Post by TSJason on 2010-11-23
haha,

well you might want to tell it to interpret a, b, and c as variables in the "total" definition. You'll also want to tell it to actually do an arithmetic operation and not just spit out the values that you just defined.

```
a=1
b=2
c=3
total=$(expr $a + $b + $c)
echo $total
```

This is only meant to get you started thinking. Don't imagine that homework assignments will be answered in any way other than how bonixavier replied.

---

### Post by nothingspecial on 2010-11-23
You`ll get in trouble doing homework here

$

---

