---
title: "bash mkdir"
date: 2012-07-26
forum: General Help
---

### Post by gishaust on 2012-07-26
hi ubuntu people,

I have been writing bash scripts but I have come to a point with mkdir command that will not work. If I am in my home dir the path I have been adding is something like  "Music" or "music"


The command from the command line

bash scriptname.sh Music

The error I get is mkdir: command not found


This is the code
```

#!/bin/bash
PATH=$1

echo $PATH;

####check directories###
if [ ! -d $PATH/sneekers ]
then
    mkdir  $PATH/sneekers
fi

```

Any direction would be great

---

### Post by Vaphell on 2012-07-26
by convention environment variables are all-caps and thus all-caps names of user variables should be avoided to prevent such situations.

you have locally overwritten an environment variable (PATH), which defines which directories are default locations to look for binaries. As soon as you changed it, mkdir became unaccessible, as PATH no longer pointed to /bin (among others) and your script doesn't know how to get there.

use lowercase path/$path to avoid confusion

---

### Post by gishaust on 2012-07-27
Thanks that solved it

---

