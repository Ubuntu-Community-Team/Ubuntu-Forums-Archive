---
title: "Bash variable substitution - single quote problems"
date: 2011-05-17
forum: General Help
---

### Post by InkyDinky on 2011-05-17
How do I perform pattern replacement of a single apostrophe in my script?
This is what I've tried to no avail. 
```


#!/bin/bash                                                                                                                                
Mens="Men's Clothing"
echo "${Mens}"
echo "${Mens/s/99}"
echo "${Mens/\0047/99}"
echo -e "${Mens/\0047/99}"
echo -e "\0047"
echo "\0047"
#the apostrophe is hex:27 oct:47                                                                                                           
echo -e "${Mens/\0047/99}"

```
This is what I get as output
```

Men's Clothing
Men'99 Clothing
Men's Clothing
Men's Clothing
'
\0047
Men's Clothing

```
I need to actually replace the single quote with two single quotes for entry into a sqlite database.

Thanks

---

### Post by papibe on 2011-05-17
Look at the new variables: this or that:
```
#!/bin/sh

Mens="Men's Clothing"
echo "${Mens}"

this=`echo $Mens | sed -e s/\'/\"/ `
echo "$this"

that=`echo $Mens | sed -e s/\'/\'\'/ `
echo "$that"
```
I hope it helps.

---

### Post by InkyDinky on 2011-05-17
I thought trying to escape with a \ wouldn't work but it does
```

echo ${Mens/\'/99}

```
the above code replaces the apostrophe / single quote.
You just can't use the " to enclose the variable. It gets expanded fine however.

---

### Post by InkyDinky on 2011-05-17
> **papibe said:**
> Look at the new variables: this or that:
```
#!/bin/sh

Mens="Men's Clothing"
echo "${Mens}"

this=`echo $Mens | sed -e s/\'/\"/ `
echo "$this"

that=`echo $Mens | sed -e s/\'/\'\'/ `
echo "$that"
```
I hope it helps.

Thanks but I was trying to do it without using sed since bash all ready has the same pattern replacement capabilities in it.

---

