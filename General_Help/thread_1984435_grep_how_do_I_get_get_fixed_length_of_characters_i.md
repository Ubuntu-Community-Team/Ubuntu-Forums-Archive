---
title: "grep_how do I get get fixed length of characters in each row"
date: 2012-05-21
forum: General Help
---

### Post by nixor01 on 2012-05-21
Hi, I want to grep a text file containing the text:

abcdef
123456
kkgghh
ssabcd

I'd want the result of only the 3rd and the 4th characters of each row and put it into a result file. How would I do that?

Thank you.

---

### Post by dcstar on 2012-05-22
> **nixor01 said:**
> Hi, I want to grep a text file containing the text:

abcdef
123456
kkgghh
ssabcd

I'd want the result of only the 3rd and the 4th characters of each row and put it into a result file. How would I do that?


What does it say in your study notes?

Perhaps if you spend some time yourself experimenting with the command you may actually learn what it does.

---

### Post by satish_j on 2012-05-22
> **nixor01 said:**
> 
I'd want the result of only the 3rd and the 4th characters of each row and put it into a result file. How would I do that?

You can use awk command here.Try foll
```

awk '{print substr($0,3,2)}' <file path>

```

---

### Post by nixor01 on 2012-05-23
That's great help satish_j, thank you very much.

---

