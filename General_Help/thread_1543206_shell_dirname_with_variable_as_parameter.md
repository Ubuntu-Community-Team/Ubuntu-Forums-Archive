---
title: "shell: dirname with variable as parameter"
date: 2010-07-31
forum: General Help
---

### Post by shade5 on 2010-07-31
Hi.

I really need help on this.

```

a=/this/is/a/dir.txt

dirname $a

```

does not work how I would like to. I tried a lot but no I am at my limit. 

Please help me.

Once this works I would like to do something like this

```

b=$(dirname $a)

mkdir -p $b

```

Many thanks,

Edit: I think I got a solution

---

### Post by worksofcraft on 2010-07-31
As far as I can see that will create the directory path /this/is/a if it doesn't exist yet, but it's not clear to me what you actually want it to do.

---

### Post by ghostdog74 on 2010-07-31
```

mkdir "${a%/*}"


```

---

