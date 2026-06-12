---
title: "shell scripting"
date: 2012-03-30
forum: General Help
---

### Post by rohit verma on 2012-03-30
how can i transpose below data
a    1    g
a    2    f
b    1    hh
b    2    df
b    3    dg

to 

id    1    2    3
a    g    f    
b    hh    df    dg

):P

---

### Post by brainwash on 2012-03-30
Hey,

I only know the basics of awk programming, but I was able write a working solution:

formatted code:
```
awk '{
    id[$2]  = $2
    key[$1] = $1
    val[$1] = sprintf("%s %s",val[$1],$3)
} END {
    printf "id "
    for (i in id)
        printf "%s ",id[i]
    printf "\n"
    for (i in val)
        print key[i] val[i]
}' input.txt
```

one-line:
```
awk '{id[$2]=$2; key[$1]=$1; val[$1]=sprintf("%s %s",val[$1],$3)} END {printf "id "; for (i in id) printf "%s ",id[i]; printf "\n"; for (i in val) print key[i] val[i]}' input.txt
```

Cheers!

---

### Post by rohit verma on 2012-04-02
thanks buddy.
it worked for me.. :)

---

