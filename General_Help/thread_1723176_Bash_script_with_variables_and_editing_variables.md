---
title: "Bash script with variables and editing variables"
date: 2011-04-06
forum: General Help
---

### Post by p014k on 2011-04-06
Hello, I'd like to make a script that would do this;

mkvmerge -o <filename without extension>_TV.mkv -S <filename>  && mkvextract tracks <filename>  3:<filename without extension>.*** && perl /home/brian/Desktop/ass2srt.pl <filename without extension>.*** && rm <filename without extension>.***

Doing these commands for multiple command line file inputs is the goal. So I can just type ./script.sh *.mkv in my terminal.

This is what I have so far, but it doesn't work whatsoever.

```

#!/bin/bash
LOOPVAR=$#
ARGS=("$@")
until [ $LOOPVAR=0 ]; do
    let $LOOPVARE=$(LOOPVAR% | cut -d'.' -f1)
    mkvmerge -o $LOOPVARE _TV.mkv -S $LOOPVAR
    mkvextract tracks $LOOPVAR 3:$LOOPVARE .***
    perl ~/Desktop/ass2perl.pl $LOOPVARE .***
    rm $LOOPVARE .***
    let LOOPVAR=LOOPVAR-1
done

```Thanks.

EDIT: the three asterisks are the 'A-word' which is a legit file extension, but alas filters.

---

### Post by sisco311 on 2011-04-06
Hi! 

Try something like:
```

#!/bin/bash

for file in "$@"               # **in "$@"** can be omitted ;) 
do
    echo "${file%.*}"          #file without suffix (or .**extension**)
    echo "${file%.*}".\a\s\s   # file with .*** suffix
done
```

Check out a good bash guide:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

parameter expansion:
[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)
and the man page of bash about  quoting:
```
man bash | less +/^QUOTING
```

---

### Post by p014k on 2011-04-07
GREAT!!! 

Thank you, that worked perfectly. I didn't know I could just do 'for file in' or the correct syntax of "${file%.*}" after reading several guides.

Thanks again!

---

