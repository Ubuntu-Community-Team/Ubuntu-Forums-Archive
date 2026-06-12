---
title: "Command Line: 'Error: This script must be run with bash'"
date: 2009-09-30
forum: General Help
---

### Post by SingingBush on 2009-09-30
can someone please explain why I'm unable to run this file.  The error states I need to use bash but as displayed by 'echo $SHELL' - I am.

root@me-ubuntu:/home/unreal/ut-server# ls -l asu.*
-rwxrwxrwx 1  900  900   1119 2002-04-25 00:24 asu.sh

root@me-ubuntu:/home/unreal/ut-server# ./asu.sh
./asu.sh: Error: This script must be run with bash

root@me-ubuntu:/home/unreal/ut-server# echo $SHELL
/bin/bash

---

### Post by wojox on 2009-09-30
The top of the script starts with:

[PHP]#!/bin/bash[/PHP]

---

### Post by ApEkV2 on 2009-09-30
> **wojox said:**
> The top of the script starts with:

[PHP]#!/bin/bash[/PHP]

That's a big solved!

---

### Post by CatKiller on 2009-09-30
Why not just run ```
bash asu.sh
```

---

