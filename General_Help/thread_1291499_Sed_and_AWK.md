---
title: "Sed and AWK"
date: 2009-10-14
forum: General Help
---

### Post by DMurray on 2009-10-14
Hi all.
I have an ASCII file with about 27 million lines. I need to process some of them at a time. Say, from 1 to 2000000, then 2000001 to 4000001, and so on.
My idea is to pass 3 arguments to the script: input file, first line, last line. The output is redirected to another file.
I wrote this code:

```

INPUT_FILE=$1
FIRST_LINE=$2
LAST_LINE=$3
IDX=$FIRST_LINE

while [ $IDX -le $LAST_LINE ]
do
   awk NR==$IDX $ARQ_ENTRADA
   IDX=`expr $IDX + 1`
done
```

It only reads the 1st line and AWK gets stuck. If I comment AWK, the index loops correctly.
If I change the line to ```
awk -v idx=$IDX 'NR==$idx $INPUT_FILE'
``` it gives a syntax error.
Using Sed does it right (and in fact sed seems to be lighter than AWK), but it doesn't return the prompt after printing the range of lines.

```

sed -n ${FIRST_LINE},${LAST_LINE}p $INPUT_FILE
```

It works, but no prompt back, it gets stuck.
I could write it in C/C++, but I don't have the compiler for the Solaris I work on.
Any idea?

Thanks a lot.

---

### Post by jonobr on 2009-10-15
I notice no responses to this, 
I recommend you put this into programming instead of general.,

The guys over there rock

---

