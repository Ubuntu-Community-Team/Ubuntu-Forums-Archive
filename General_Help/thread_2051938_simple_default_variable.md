---
title: "simple default variable"
date: 2012-09-02
forum: General Help
---

### Post by sselt on 2012-09-02
I know this is not correct. I want the option variable to be the default if the option is not given on the command line.

```
#!/bin/bash

foo2option=1
foo1 $(foo2 --foo2option $2 $1)

```Running the script with no option:
```
$ ./script somefile
```would run:
 ```
foo1 $(foo2 --foo2option 1 somefile)
```Running the script with an option:
```
$ ./script somefile 2
```would run:
```
foo1 $(foo2 --foo2option 2 somefile)
```

---

### Post by steeldriver on 2012-09-02
Have a look at the bash

```
${parameter-default}, ${parameter:-default}
```syntax - that should do it - something like

```
#!/bin/bash

default=2

echo command $1 ${2:-$default}
```will use the 2nd command line argument $2 if it is set, and $default otherwise

[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

I hope this is legal! if not I'm sure one of the real bashistas will step in and correct me

---

### Post by sselt on 2012-09-02
> **steeldriver said:**
> will use the 2nd command line argument $2 if it is set, and $default otherwise

[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

I hope this is legal! if not I'm sure one of the real bashistas will step in and correct me

Perfect! Thanks steeldriver. I need to read more about syntax. I'm marking this solved. If anyone still wants to throw in other ideas, feel free.

---

