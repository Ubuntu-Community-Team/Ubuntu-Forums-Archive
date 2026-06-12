---
title: "how do I set the sticky bit?"
date: 2012-01-21
forum: General Help
---

### Post by conradin on 2012-01-21
Hi All,
I wrote some code that directly accesses hardware but I still get iopl errors. Ive been reading and I think setting the sticky-bit could be what I need to do to make my programs run correctly.

So how do I set the sticky bit?

---

### Post by WorMzy on 2012-01-21
```
chmod +t /path/to/directory-or-directory
```

---

### Post by conradin on 2012-01-21
Thanks wormzy that does set the sticky bit,
I think what Im actualy trying to do is set the psermissions to something like:
-r-s--x--x
have any idea how to do that?

---

### Post by conradin on 2012-01-21
using stupid brute force, i figured it out with code
```

#!/bin/bash
for i in `seq 0 7777`;
do
	chmod $i '/usr/students/elovejoy/Desktop/bj'
	echo $i ":" `ls -l '/usr/students/j/Desktop/bj'` >> modes
	echo
done

```
Then searched that output file for "-r-S--x--x"
So i think```
chmod 4411 <file> 
```
will work.

---

### Post by WorMzy on 2012-01-22
That's the setuid bit, and you can set it with ```
chmod u+s
```

Similarly, you can set the setgid bit with ```
chmod g+s
```

Or you can use octal, like you've been experimenting with:

1 = Sticky bit
2 = Setgid bit
4 = Setuid bit

---

