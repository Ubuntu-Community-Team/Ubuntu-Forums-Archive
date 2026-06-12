---
title: "command question"
date: 2010-01-07
forum: General Help
---

### Post by Drenriza on 2010-01-07
Is it possible to type & execute more then 1 command in 1 sentence? 
and how?

---

### Post by amauk on 2010-01-07
```
echo "Yes it's possible"; echo "Just use semicolons to separate commands"; echo -n "Your current kernel is "; echo `uname -r`; echo "Goodbye"
```

---

### Post by howefield on 2010-01-07
Use a colon eg

```
sudo apt-get update ; sudo apt-get install whatever
```

The command is carried out in order, even if there is an error in the first one.

Use && eg,

```
sudo apt-get update && sudo apt-get install whatever
```

The second command is carried out only if the first was successful.

---

### Post by stinkeye on 2010-01-07
> **amauk said:**
> ```
echo "Yes it's possible"; echo "Just use semicolons to separate commands"; echo -n "Your current kernel is "; echo `uname -r`; echo "Goodbye"
```

Best answer I've seen in a while.
=D>:-P

---

### Post by nikhilbhardwaj on 2010-01-07
> **howefield said:**
> Use a _**colon**_ eg

```
sudo apt-get update ; sudo apt-get install whatever
```The command is carried out in order, even if there is an error in the first one.


you mean semi-colon

---

### Post by howefield on 2010-01-07
> **nikhilbhardwaj said:**
> you mean **semi-colon**

Of course.

---

### Post by Drenriza on 2010-01-08
Thanks alot guys.

---

