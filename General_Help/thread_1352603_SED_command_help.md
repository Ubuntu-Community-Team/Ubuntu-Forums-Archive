---
title: "SED command help"
date: 2009-12-11
forum: General Help
---

### Post by beekr on 2009-12-11
Can anyone help break down the following sed command for me? Can't figure it out. 

sed '/([0-9]*)$/N; s/)\n/)/'


Thanks,
Beekr

---

### Post by audiomick on 2009-12-11
Have you looked at the man page?
```
man sed
```

It looks like it is all in there, but it is 3 a.m. here, and I can't make sense of it...;)

---

### Post by DaithiF on 2009-12-12
it accomplishes nothing, so far as I can see...

/(0-9)*$/  matches lines ending with a number enclosed in brackets, e.g.
```
some line (15)
another line (1045)

```the N reads in the next line of output, appending it to the line currently being processed.
so if you had two lines:
```
some line (15)
next line

```then at this point in the sed expression these will have been joined:
```
some line (15)next line
```and now the s/)/)\n/ matches the ')' and replaces it with ) and a newline, which means you're back where you started

probably theres some subtlety i'm missing, perhaps if there is an example file it was written to operate on it might be more obvious.

---

### Post by DaithiF on 2009-12-12
actually, i mis-read the s// expression at the end, in fact its matching )\n and replacing it with just ), so in effect its leaving these 2 lines joined.

so in my example the output would be: some line (15)next line

so basically its looking for lines ending with numbers in brackets, and joining those with the lines just after.

---

### Post by beekr on 2009-12-12
this SED command was used while CATing a file. We needed the date and time stamp. Here is the whole command used:

 cat xxxxx_2009_01_12.log | sed '/([0-9]*)$/N; s/)\n/)/' | grep -iE "xxxxxxx"


Hope this helps.

---

