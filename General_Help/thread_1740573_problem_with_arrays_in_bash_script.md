---
title: "problem with arrays in bash script"
date: 2011-04-27
forum: General Help
---

### Post by mahmoodn on 2011-04-27
I want to work with an array element by element in bash script. Here is what I wrote:
```

#!/bin/bash
NAMES=( name1 name2 name3 )

for i in ${NAMES}
do
   NAME=${NAMES[@]:$i:(($i+1))}
   echo $NAME
done

```

However this is what get:
```
name1
```

I expect
```
name1
name2
name3
```

---

### Post by sisco311 on 2011-04-27
[http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005)

---

### Post by paul_will on 2011-04-27
Try 

```
NAMES=(name1 name2 name3)
for n in ${NAMES[@]};do echo $n;done
```

Not sure where you were going with your script but this gets me your desired result.

---

### Post by mahmoodn on 2011-04-27
Thanks for the link and thanks for the short answer. :)

---

