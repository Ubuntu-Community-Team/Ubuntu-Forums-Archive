---
title: "unrar script needed"
date: 2010-06-17
forum: General Help
---

### Post by Comish on 2010-06-17
Hey Peeps, So i have a home server that i download alot of files onto and these files are always in multi part rars so i need a script to extract all the rar files in all folders/sub folders then delete the rar file leaving the extracted file. Im running ubuntu server 10.04. 
Thanks very much Comish.

---

### Post by sdennie on 2010-06-17
I think this will do what you want:

```


#!/bin/bash

BASE=.

for file in `find $BASE -name "*.r00"`; do
    cd `dirname $file`
    rar e `basename $file` &&  rm *.r??
done

```

It should be safe to run as it only deletes the rar parts if the extraction returns successfully.

---

### Post by Comish on 2010-06-17
Will this also work with .part1.rar files? thanks comish

---

### Post by doas777 on 2010-06-17
no, but it would be really easy to modify the Find line to accomodate```
find $BASE -name "*.part1.rar"

```lmk if you come up with some par2 integration. that'd be kinda kewl

also, be careful if the uncompressed file extension starts with r, it will get deleted too

---

### Post by Comish on 2010-06-17
So to include both would it be somthing like this
```
#!/bin/bash

BASE=.

for file in `find $BASE -name "*.r00,*.part01.rar"`; do
    cd `dirname $file`
    rar e `basename $file` &&  rm *.r??
done
```

im still abit of a noob to this sort of thing lol.

Thanks.

---

### Post by Comish on 2010-06-17
Bump.

---

### Post by doas777 on 2010-06-18
since I am no expert with the find command, I would probably do it in two successive blocks rather than concatenating on the additional find parameters.
```

#!/bin/bash

BASE=.

for file in `find $BASE -name "*.r00"`; do
    cd `dirname $file`
    rar e `basename $file` &&  rm *.r??
done
for file in `find $BASE -name "*.part01.rar"`; do
    cd `dirname $file`
    rar e `basename $file` &&  rm *.r??
done

```

---

