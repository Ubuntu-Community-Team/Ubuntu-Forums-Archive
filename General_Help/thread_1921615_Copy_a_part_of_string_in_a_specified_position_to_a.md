---
title: "Copy a part of string in a specified position to another position in the same string?"
date: 2012-02-07
forum: General Help
---

### Post by the_X_files on 2012-02-07
If I have the following output from a script
```
TEST1 TEST23 TEST785
TEST1 TEST99 TEST78
```
I want to copy symbols from 11-12 position after 5 position so my string look like that
```
TEST123 TEST23 TEST785
TEST199 TEST99 TEST78
```

---

### Post by dcstar on 2012-02-07
> **the_X_files said:**
> If I have the following output from a script
```
TEST1 TEST23 TEST785
TEST1 TEST99 TEST78
```
I want to copy symbols from 11-12 position after 5 position so my string look like that
```
TEST123 TEST23 TEST785
TEST199 TEST99 TEST78
```

Homework eh?

---

### Post by Khayyam on 2012-02-07
> **dcstar said:**
> Homework eh?

dcstar ...

probably, by the looks of the strings ("TEST" is a bit of a giveaway).  Anyhow, such things can backfire as homework is generally set on  material already covered in the class and not the most elegant solution  to the problem. So, "cheating" simply raises a red flag .. 

Anyhow .. my solution:

```
cat input.txt |awk '{print $1(substr($2,5,6)), $2 , $3}' > output.txt
```

---

