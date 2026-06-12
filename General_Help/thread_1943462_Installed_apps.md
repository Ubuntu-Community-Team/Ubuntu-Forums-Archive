---
title: "Installed apps"
date: 2012-03-19
forum: General Help
---

### Post by Gwaro on 2012-03-19
Is there a way to get the total number of applications installed in your system from the command line?

---

### Post by TeoBigusGeekus on 2012-03-19
```
dpkg -l | wc -l
```

---

### Post by Gwaro on 2012-03-19
> **TeoBigusGeekus said:**
> ```
dpkg -l | wc -l
```


Perfect! Thanks alot:popcorn:

---

### Post by TeoBigusGeekus on 2012-03-19
You're welcome; don't forget to mark the thread as solved.

---

### Post by Gwaro on 2012-03-19
> **TeoBigusGeekus said:**
> ```
dpkg -l | wc -l
```

Can this be applied also in counting the number of characters in a string(say a word or a sentence)?

---

### Post by TeoBigusGeekus on 2012-03-19
Yes of course.
```
echo TeoBigusGeekus | wc -m
15
```
Run 
```
man wc
```
for more info.

---

### Post by Gwaro on 2012-03-19
> **TeoBigusGeekus said:**
> Yes of course.
```
echo TeoBigusGeekus | wc -m
15
```Run 
```
man wc
```for more info.


Am grateful.

---

