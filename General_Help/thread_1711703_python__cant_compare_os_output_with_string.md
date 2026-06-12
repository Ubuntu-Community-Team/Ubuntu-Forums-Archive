---
title: "python : cant compare os output with string"
date: 2011-03-21
forum: General Help
---

### Post by d3v1150m471c on 2011-03-21
i have something like this:
```

this = os.popen("echo 12345")
this = this.readline()
test = "12345"
if test == this:
 print "works..."
 sys.exit(0)

```

this doesn't work, any advice?

---

### Post by WorMzy on 2011-03-21
```
>>> import os
>>> this = os.popen("echo 12345")
>>> this = this.readline()
>>> print(this)
12345

>>> test = "12345"
>>> print(test)
12345
>>>
```
Note the newline in *this*.

use echo -n as your popen command instead.

---

### Post by d3v1150m471c on 2011-03-21
i should have mentioned this earlier but i forgot. i'm trying to test if the output of os.popen(command) contains the contents of a variable. IE

test = something
os.popen's output = this is something here

if os.popen's output == test:
 this would come up as "True"

---

### Post by WorMzy on 2011-03-21
That's not what == does. 

I'm not a python expert, but __contains__ seems to do what you want.

```
>>> import os
>>> this = os.popen("echo hello")
>>> this = this.readline()
>>> test = "hello"
>>> print(this)
hello

>>> print(test)
hello
>>> if this.__contains__(test):
...   print("YES")
...
YES
>>> test = "goodbye"
>>> if this.__contains__(test):
...   print("YES")
...
>>>

```

Any good?

---

### Post by d3v1150m471c on 2011-03-21
that's perfect! does exactly what i need it to do. thanks a bunch :)

---

