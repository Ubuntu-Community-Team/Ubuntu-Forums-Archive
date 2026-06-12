---
title: "Variable Rename"
date: 2010-02-09
forum: General Help
---

### Post by Chamillionaire2 on 2010-02-09
What's Up?

OK, So I have a small problem, For my latest project in bash I need to be able to rename some ttext files to a varied name, I tried using this.
```

date=date
mv txt.txt $date

```
But mv doesn't like using variables, And I can't seem to figure out how to use 'Rename' seems a bit harder to do then it needs to be.

Anyone point me into the right direction?

Thanks Bye.

---

### Post by Chamillionaire2 on 2010-02-09
As soon as I posted this I found '$RANDOM' I have another question, Why am I such an idiot? :D

---

### Post by kaibob on 2010-02-09
The mv command accepts variables without any issue.

Are you trying to get a "varied name" by use of the date command? If so, you have to use command substitution, as in the following:

> $ mv file.txt $(date +%m.%d.%y_at_%H.%M.%S).txt
$ ls
02.09.10_at_17.59.25.txt

See the date man page for formatting and other options.

---

