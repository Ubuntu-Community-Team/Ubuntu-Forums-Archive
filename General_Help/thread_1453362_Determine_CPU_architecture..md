---
title: "Determine CPU architecture."
date: 2010-04-13
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-04-13
I need to determine my exact CPU architecture, i know there are several x86, x86-64, i686, etc, i know i686 is just an extended instruction set of x86. but how do i determine mine exactly?

uname -p or uname -i just return 'unknown'
/proc/cpuinfo also returns not very helpful info.

Thanks.

---

### Post by wojox on 2010-04-13
Try:

```
sudo lshw | grep cpu
```

---

### Post by warfacegod on 2010-04-13
```
uname -m
```

That should tell you exactly what you want to know.

---

### Post by NiGhtMarEs0nWax on 2010-04-13
> uname -m

Thanks for the input guys, that is exactly what i was looking for. :)

---

### Post by warfacegod on 2010-04-13
Glad to help. There are other uses for uname as well.

```
man uname
```

will give you a list of options for it.

---

