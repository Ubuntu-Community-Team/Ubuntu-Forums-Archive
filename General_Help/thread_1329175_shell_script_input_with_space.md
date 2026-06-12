---
title: "shell script input with space"
date: 2009-11-17
forum: General Help
---

### Post by skaldyr on 2009-11-17
i have this function in a shell script

```
exiftool -DateTimeOriginal=$1 ft.jpg
```

the $1 should be in this format  '2009:01:01 02:03:04'

i have search google but i cant find a solution that works

---

### Post by slakkie on 2009-11-17
If you expect one param:

```

#!/usr/bin/env bash

echo $1

```

```

bash x.sh "test 123"
test 123

```

Or you can use:

echo $@

then you can run bash x.sh test 123

which will output the same.

---

### Post by skaldyr on 2009-11-17
thanks for the reply.

i found a way i just use "$1" and it works one hours work for two " 

:p

---

