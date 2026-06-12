---
title: "Mass find cp"
date: 2012-05-09
forum: General Help
---

### Post by craigp on 2012-05-09
What I'm looking to do is search for .htaccess2 files and replace all .htaccess files with .htaccess2 files in the same directory.


find /home/ -iname ".htaccess2" -exec cp {} {} \;

This command will find all of the .htaccess2 files inside of /home/ but when it copies the file it just copies it to the same name.

Trying
find /home/ -iname ".htaccess2" -exec cp {} .htaccess \;
just puts it in the current directory i was in and not in the same directory as the .htaccess2 file.

Any help would be appreciated.

---

### Post by steeldriver on 2012-05-09
it's a bit of a kludge, but I think you could create a little shell script to do the actually copy, something like

```

#!/bin/bash
cp $1 ${1%2}

```and then do

```
find /home/ -iname ".htaccess2" -exec ./myscript {} \;
```Hope this helps

---

### Post by craigp on 2012-05-10
Awesome, that worked perfectly. Thank you

---

### Post by steeldriver on 2012-05-10
happy to help

if it's more than a one-time thing, you should probably consider testing whether htaccess exists (if that matters - cp won't care), and maybe even backing it up (ditto)

---

