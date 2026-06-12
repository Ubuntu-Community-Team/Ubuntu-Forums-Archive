---
title: "Append something at the end of a text file WITHOUT adding it to a new line"
date: 2009-08-05
forum: General Help
---

### Post by lethalfang on 2009-08-05
Say, if I have a textfile.txt, and I want to add something to the last line of textfile.txt.

The following command:
echo 'something' >> textfile.txt will create a new line in the text file and write "something" to it.

What if I want the "something" appended to the last line of the text file without creating a new line?

Looking at "man echo," I tried to add a backspace right before "something," (\b means backspace), but the following command doesn't work either:
echo -e '\bsomething' >> textfile.txt

What is a good way to do it?

Thanks in advance.

---

### Post by wojox on 2009-08-05
Usse sed:

```
sed '$s/$/&something/' textfile.txt
```

---

### Post by lethalfang on 2009-08-05
Thanks. That works well.
..... one of these days, I'll need to learn more about sed and awk. Lots of problems I've had recently all seem to point to one of them. :popcorn:

> **wojox said:**
> Usse sed:

```
sed '$s/$/&something/' textfile.txt
```

---

