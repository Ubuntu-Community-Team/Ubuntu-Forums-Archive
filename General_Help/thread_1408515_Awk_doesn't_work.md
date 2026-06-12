---
title: "Awk doesn't work"
date: 2010-02-16
forum: General Help
---

### Post by fborcic on 2010-02-16
Hello,
i have a list of numbers, and i'm trying to get them, separated by periods three in one line.
I used this script:
```
BEGIN {FS="\n"; RS=""}
{
        print $1 ", " $2 ", " $3 ","
}

```as most tutorials say that will work, but awk outputs only first line.
Sed either does not work correctly, i can't use delete function.
I tried mawk and gawk and nothing is working.
                                             Thanks,
                                                     Fran

---

### Post by CaKiwi on 2010-02-16
Try

```

BEGIN {FS="\n"; RS=""}
{
  for (i=1;i<=NF;i+=3)
    print $i ", " $(i+1) ", " $(i+2) ","
}
```

---

