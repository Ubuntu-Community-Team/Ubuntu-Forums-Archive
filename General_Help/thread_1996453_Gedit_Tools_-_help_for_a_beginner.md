---
title: "Gedit Tools - help for a beginner"
date: 2012-06-04
forum: General Help
---

### Post by jby601 on 2012-06-04
I am a relative new-comer to the wonderful world of unix/linux, and would like an explanation of one aspect in a few lines of code that form part of the 'Build' tool in gedit.

At the top of the file these lines appear:

#!/bin/sh
EHOME=`echo $HOME | sed "s/#/\#/"`
DIR=$GEDIT_CURRENT_DOCUMENT_DIR
while test "$DIR" != "/"; do
    for m in GNUmakefile makefile Makefile; do
        if [ -f "${DIR}/${m}" ]; then
            echo "Using ${m} from ${DIR}" | sed "s#$EHOME#~#" > /dev/stderr
...........

My question: what is the action of the sed substitution of # by \# ? Why is the second # escaped? Sometimes the simplest things are the hardest to understand!

---

### Post by Vaphell on 2012-06-04
i think that it is a failed attempt to escape existing # to make sure it is not confused with delimiters down the road, where the $HOME is supposed to be shorthanded to ~. It doesn't seem to be working.
The author should have used some forbidden char as far as filesystems are concerned ( ?*|:... ) as a delimiter to be sure that there is no collision, which would eliminate the need of escaping in the first place and on top of that single \ doesn't do a thing, not to mention that sed misses /g (perform multiple substitutions).

```
$ a=abc###
$ b=$( echo ${a} | sed 's/#/\#/' )
$ c=$( echo ${a} | sed 's/#/\\#/' )
$ echo ${#a} ${#b} ${#c}
6 6 7
```

---

### Post by jby601 on 2012-06-04
Thank you very much for your helpful reply - somehow one automatically trusts other people to have written good code!

---

