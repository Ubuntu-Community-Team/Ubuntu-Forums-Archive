---
title: "how to user a var in bash"
date: 2010-03-04
forum: General Help
---

### Post by b-boy on 2010-03-04
hi 

how can i write this
```

#!/bin/bash
foo=`find / -iname xeyes`
dpkg -i $foo
```

in bash not in a script

something like this

```
$`find / -iname xeyes`|dpkg -i $1
```


i know the above code is wrong please help

---

### Post by bluefrog on 2010-03-04
find somewhere something -exec command {} \;

---

### Post by psusi on 2010-03-04
That script IS bash.  And variables just get replaces with whatever you set them to, so if you don't want to use the variable, then just replace it with what you set it to:

dpkg -i `find / -iname xeyes`

---

### Post by b-boy on 2010-03-05
> **psusi said:**
> That script IS bash.  And variables just get replaces with whatever you set them to, so if you don't want to use the variable, then just replace it with what you set it to:

dpkg -i `find / -iname xeyes`

nice one Thanks

---

### Post by mcduck on 2010-03-05
For future reference, if you write Bash scripts then it's exactly the same as if you were writing the commands directly in Bash.

Anyway, you can use a semicolon to separate each command from each other.

```
foo=`find / -iname xeyes`; dpkg -i $foo
```

---

