---
title: "using sed/awk"
date: 2010-09-30
forum: General Help
---

### Post by hinge on 2010-09-30
I am really a clown when it comes to using awk and sed...I need help:

I need to transform this string:
```
"20000214_143544.jpg"
```
to this:
```
"2000:02:14 14:35:44"
```

How do I sed/awk that?

Thanks

---

### Post by gmargo on 2010-09-30
How about perl?
```

echo "20000214_143544.jpg" | perl -ne 's/(\d{4})(\d{2})(\d{2})_(\d{2})(\d{2})(\d{2}).jpg/$1:$2:$3 $4:$5:$6/;print'
2000:02:14 14:35:44

```

---

### Post by hinge on 2010-09-30
Waaoo...

Thanks

---

### Post by gmargo on 2010-09-30
The equivalent in sed.  Lots more backslashes:
```

$ echo "20000214_143544.jpg" | sed 's/^\([0-9]\{4\}\)\([0-9]\{2\}\)\([0-9]\{2\}\)_\([0-9]\{2\}\)\([0-9]\{2\}\)\([0-9]\{2\}\).*/\1:\2:\3 \4:\5:\6/'
2000:02:14 14:35:44

```

---

### Post by DaithiF on 2010-09-30
> **gmargo said:**
> The equivalent in sed.  Lots more backslashes:
```

$ echo "20000214_143544.jpg" | sed 's/^\([0-9]\{4\}\)\([0-9]\{2\}\)\([0-9]\{2\}\)_\([0-9]\{2\}\)\([0-9]\{2\}\)\([0-9]\{2\}\).*/\1:\2:\3 \4:\5:\6/'
2000:02:14 14:35:44

```
a good candidate for using the sed -r extended regular expression flag ... no need to escape the ( ) { } characters, so a lot less backslashes
```
$ echo "20000214_143544.jpg" | sed -r 's/^([0-9]{4})([0-9]{2})([0-9]{2})_([0-9]{2})([0-9]{2})([0-9]{2})/\1:\2:\3 \4:\5:\6/'
2000:02:14 14:35:44

```

and if you can be sure that all strings follow this pattern you could remove the [0-9] character class pattern and just use . instead for another shortening in the pattern length: 
```
$ echo "20000214_143544.jpg" | sed -r 's/^(....)(..)(..)_(..)(..)(..)/\1:\2:\
3 \4:\5:\6/'
2000:02:14 14:35:44

```

---

