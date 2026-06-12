---
title: "help with md5sum"
date: 2011-04-27
forum: General Help
---

### Post by duckyq on 2011-04-27
Hi, im having some trouble with Md5sum, when i run ```
echo -n AlBgNb5Q5gic | md5sum
``` i get the hashed string with 3 white spaces and a dash, how do i remove the 3 whitespaces and dash? I need it to match with md5 over at mysql server but it fails, i'm guessing the problem is with the whitespaces and the dash
 
thanks
 
SOLVED:```
 echo -n AlBgNb5Q5gic | md5sum | cut -f1 -d' '
```

---

### Post by pqwoerituytrueiwoq on 2011-04-27
i assume this is in a script
there is a substr function in the expr command
```
expr substr abcdef 1 3
```since a md5sum is always 32 characters we can change the 3 to 32
then you just have to pass the md5sum to the expr command
edit
```
expr substr "`echo -n AlBgNb5Q5gic | md5sum`" 1 32
```

---

### Post by duckyq on 2011-04-27
thanks for the reply, just by adding  cut -f1 -d' ' at the end of the command will remove the whitespaces and dash

---

