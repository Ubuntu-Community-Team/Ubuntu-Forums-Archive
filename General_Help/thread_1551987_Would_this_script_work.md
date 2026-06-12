---
title: "Would this script work?"
date: 2010-08-13
forum: General Help
---

### Post by redfox1160 on 2010-08-13
I was wondering, would this script touch the file then delete itself? Thanks.
```
#!/bin/bash
touch file.txt
rm thisscript.sh
```

---

### Post by worksofcraft on 2010-08-13
Why don't you try it ?
Then you will know.

p.s. OK I won't keep you in suspense... yes it work fine, but why even ask is what I want to know :P

---

### Post by Spice Weasel on 2010-08-13
Yep.

---

### Post by KeyserSoze93 on 2010-08-13
> **redfox1160 said:**
> I was wondering, would this script touch the file then delete itself? Thanks.
```
#!/bin/bash
touch file.txt
rm thisscript.sh
```

Try changing it to:

```
rm $0
```

The shell sets $0 to the name of the current script, which means that if you change the name or run it from a different directory, it will still work.

---

### Post by redfox1160 on 2010-08-13
Thanks. I couldn't try it because I wasn't at a Ubuntu computer at the time.

---

