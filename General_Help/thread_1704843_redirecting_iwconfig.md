---
title: "redirecting iwconfig"
date: 2011-03-11
forum: General Help
---

### Post by Hippytaff on 2011-03-11
When iwconfig is redirected thus```
 iwconfig >> wireless.txt
```
 
things like ```
eth0 - Has no wireles extension
``` are still outputted to the terminal (stdout)
 
How come?

---

### Post by Charlietje on 2011-03-11
This is because you only redirected stdout the the text file
You didn't redirect the err output to the textfile


it should be:

```
iwconfig 1> wireless.txt 2>&1
```

---

### Post by Hippytaff on 2011-03-11
Excellent...thanks

I wanted to send the other output err to /dev/null
```

iwconfig 1>>wireless.txt 2> /dev/null

```

I couldn't have done it without you man!

---

