---
title: "Tcsh - writing grep output into variable"
date: 2011-10-08
forum: General Help
---

### Post by xqwzts on 2011-10-08
Hello,
I am writing certain tcsh script and I would like to write grep command (echo "<some number>" | egrep -c '^-?[0-9]+[.]?[0-9]*$') result into the variable and then use it inside "if". I would be very grateful for any clue that would help me solve this problem. 

In bash I could do this like this: $variable = $(echo "1.23423" | egrep -c '^-?[0-9]+[.]?[0-9]*$')

but how can I do it in tcsh ?

---

### Post by WasMeHere on 2011-10-08
Try the following command
```
set variable=`echo "1.23423" | egrep -c '^-?[0-9]+[.]?[0-9]*$'`
```

Have fun
Olle

---

