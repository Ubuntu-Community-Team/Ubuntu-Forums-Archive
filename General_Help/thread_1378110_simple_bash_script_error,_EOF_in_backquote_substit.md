---
title: "simple bash script error, EOF in backquote substitution"
date: 2010-01-11
forum: General Help
---

### Post by readycarpenter on 2010-01-11
so im trying to loop and run these 2 commands on each folder in indir
and get the folder name as a variable, i get this error

bookbatch.sh: 27: Syntax error: EOF in backquote substitution

and here is the script...
```
#!/bin/bash
indir="/media/MaxtorOneTouchIII/Audiobooks/Robert Jordan"

for bookdir in "$indir"/*
do
   title=`basename "$bookdir"
   python mp3reencode.py -s 44.1 -b 64 -c j -d "$bookdir"
   mp3wrap ../$title.mp3 *_REENCODED_.mp3
done
#End of File
```

---

### Post by DaithiF on 2010-01-11
```
title=`basename "$bookdir"

```
you don't close this expression with a second backtick.  

So:
```
title=`basename "$bookdir"`

```
or arguably better (use $( ) rather than backticks to execute an external command):
```
title=$(basename "$bookdir")
```

---

### Post by readycarpenter on 2010-01-11
thanks  title=$(basename "$bookdir") did the trick ;)

---

