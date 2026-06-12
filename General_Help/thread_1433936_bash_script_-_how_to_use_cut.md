---
title: "bash script - how to use cut"
date: 2010-03-19
forum: General Help
---

### Post by Vyder on 2010-03-19
For example, ive got a string:

line="one two three four-five six:seven eight"

and i want to split them at the " " and get the third part - "three"

would it be:

```
`echo line | cut -d" " -f3`
```

---

### Post by jobix on 2010-03-19
That's right. Almost. You just need to provide the $ so that it reads "echo $line" instead of "echo line". "echo line" will simply print "line". What you need is the value of line which is denoted by the "$".

The "-d" is for the delimiter, in this case " ". The "-f" is for the field, in this case field number 3. On the other hand, if you wanted to extract out "seven", you'd cut based on ":" and ask for field number 2 since everything before the ":" is one field and everything after it is another field. However, as you'll quickly realize field 2 will give you "seven eight" and so you'll need to pass that to a new cut command with " " as delimiter and ask for field 1.

> echo $line | cut -d":" -f2 | cut -d" " -f1


---

### Post by Vyder on 2010-03-19
oh wow...i can't believe i missed that.

Thanks for explaining how cut works.

---

