---
title: "(js and) bash functions"
date: 2012-06-07
forum: General Help
---

### Post by maclenin on 2012-06-07
Just a quick question - re: bash functions.

A. In **javascript** I can use the color(x) function to "write" either "this is red" or "this is green"...
```
**javascript**
var r="this is red";
var g="this is green";
function color(x) {document.write(x);}

**html**
<body onload="color(r);"></body>
```
...by passing either the r (or g) variable / parameter to the color(x) function.


B. How do I do the same in **bash**? How do I pass the $r variable / parameter to the color() function?

```
**#!/bin/bash**

#var
r="this is red"
g="this is green"

color()
{
echo $r
}

color $r 
#color $g

exit

```

Thanks for any guidance!

---

### Post by sisco311 on 2012-06-07
[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)

```
color (){
printf '%s\n' "$1"
}
```

---

### Post by maclenin on 2012-06-07
**sisco311!**

Thanks for your reply. This (for testing purposes) is what finally worked for me:

```

#!/bin/bash

#var
r="this is red"
g="this is green"

color()
{
echo "$1"
**# or echo "$@"**
}

#color "$r"
**# or color $r**
color "$g"
**# or color $g**
```

Yielding...

```
this is green
```

...in the terminal.

**Residual questions:**

1. Why do I have to wrap the $r and $g arguments / variables / parameters in **""** to get "this is green"? What do the **""** do to the variable?

2. If I don't wrap the $r and $g in **""** the code / function would yield...

```
this
```

...echo "$2" would yield "is" and echo "$3" would yield "green"....

Additional [reference]("http://www.ibm.com/developerworks/library/l-bash-parameters/index.html").

Thanks, again!

---

### Post by devxdev on 2012-06-07
> **maclenin said:**
> 

**Residual questions:**

1. Why do I have to wrap the $r and $g arguments / variables / parameters in **""** to get "this is green"? What do the **""** do to the variable?

2. If I don't wrap the $r and $g in **""** the code / function would yield...

```
this
```

...echo "$2" would yield "is" and echo "$3" would yield "green"....

Additional [reference]("http://www.ibm.com/developerworks/library/l-bash-parameters/index.html").

Thanks, again!

If its not in quotes its like passing n args to it (n == number of words in the r or g variable) hints how each time it would return a different character. As for the numbers e.g. $1, $2, $3,... think of it like this
```
color($1, $2, $3, ...)
color("this", "is", "red")
```

In PHP you could thing of it as func_get_args();

Did I confuse you?

---

### Post by sisco311 on 2012-06-07
r and g are the variables. $r and $g are variable expansions. Variable expansion is the substitution of a variable by its value.

The purpose of the quotes is to prevent word splitting. Without the quotes $r and $g would be split in three words, and each word wilould be passed to the color function. 

See:
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)
and
[http://mywiki.wooledge.org/WordSplitting](http://mywiki.wooledge.org/WordSplitting)

---

