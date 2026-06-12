---
title: "Delete all text before period"
date: 2011-06-07
forum: General Help
---

### Post by jeremy-nsa on 2011-06-07
Hello,

I have a file like this:

Subnet Server.wifi-global
Start Address = 10.10.0.1
ABCD-Admin-General.ABCD-Admin-General
Start Address = 10.10.0.2

I would like to use sed or similar to remove everything before the period, but only for the lines 1 and 3 (or lines with a-z.a-z and not a-z = 0-9.0-9.0-9.0-9)

I found a way to do this using:

cat $file | sed 's/[.].*//'

But this 1)remove all the text AFTER the period and not before it, and 2) removes everything after the first decimal of the IP address.

Any help would be greatly appreciated!

Thanks

---

### Post by TeoBigusGeekus on 2011-06-08
Try this
```
cat $file | grep -v = | sed 's/^.*\.//g'
```

---

### Post by nothingspecial on 2011-06-08
> **TeoBigusGeekus said:**
> Try this
```
cat $file | grep -v = | sed 's/^.*\.//g'
```

Don't do that -

----- gah, I have to go now. I need to sort my kids out. I'll check back later.

```
$ cat test.txt

Subnet Server.wifi-global
Start Address = 10.10.0.1
ABCD-Admin-General.ABCD-Admin-General
Start Address = 10.10.0.2


$cat test.txt | grep -v = | sed 's/^.*\.//g'

wifi-global
ABCD-Admin-General
```

Not the desired effect. Give me a couple of hours, I have stories to read :popcorn:

---

### Post by TeoBigusGeekus on 2011-06-08
Did I miss something? That's what the op asked for.

---

### Post by nothingspecial on 2011-06-08
Couple of minutes after child2's story while child1 brushes teeth.

Maybe you are right. :)

I took the question to mean the op wanted this result

```
.wifi-global
Start Address = 10.10.0.1
.ABCD-Admin-General
Start Address = 10.10.0.2
```

> 
I would like to use sed or similar to remove everything before the period, but only for the lines 1 and 3

No offence meant Teo

---

### Post by TeoBigusGeekus on 2011-06-08
Non taken mate...
The op must make clear though what he wants.

---

### Post by sisco311 on 2011-06-08
> **nothingspecial said:**
> 

I took the question to mean the op wanted this result

```
.wifi-global
Start Address = 10.10.0.1
.ABCD-Admin-General
Start Address = 10.10.0.2
```


Then:
```

sed  '/=/! s/^.*\.//g' file

```
should do it.

---

### Post by TeoBigusGeekus on 2011-06-08
...or
```
sed '/.*=/b;s/^.*\./\./g' file
```

---

### Post by jeremy-nsa on 2011-06-08
Ahh thank you very much!

sed '/.*=/b;s/^.*\./\./g' file worked perfectly!

 - Jeremy

---

### Post by TeoBigusGeekus on 2011-06-08
You're welcome and don't forget to mark the thread as solved.

---

### Post by nothingspecial on 2011-06-08
nevermind

---

### Post by jeremy-nsa on 2011-06-16
Hello,

Thank you all very much for the replies. I have successfully edited out what I needed to!

Take care

---

### Post by sisco311 on 2011-06-16
Cool!

Don't forget to mark this thread as [SOLVED].

---

