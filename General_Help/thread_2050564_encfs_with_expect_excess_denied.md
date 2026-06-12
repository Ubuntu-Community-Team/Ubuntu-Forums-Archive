---
title: "encfs with expect excess denied"
date: 2012-08-31
forum: General Help
---

### Post by zoloto on 2012-08-31
If I execute script
```
#!/usr/bin/expect 
set pass [lindex $argv 0] 
spawn encfs -v  {CRIPT_DIR}  {MNT_DIR} -o nonempty 
expect "*EncFS Password:*"
send "$pass\r"
expect eof
```I don't have access to {MNT_DIR}. Sodo user don't have access to. But command or shell scipt 
```

#!/bin/sh
encfs -v  {CRIPT_DIR}  {MNT_DIR} -o nonempty 
```work correct.

What is wrong in my expect script?

---

