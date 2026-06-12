---
title: "bash output redirection"
date: 2010-01-13
forum: General Help
---

### Post by prem1er on 2010-01-13
I would like to output an echo to the same line as the results of a db2 query instead of both being printed on separate lines. Here is an example if I am not clear.

```
   
   if [ "$_input" != "$_temp" ]; then
      echo "$_input, " >> $_dataFile
   fi

   db2 -x "select statement" | sed 's/  */,/g' >> $_dataFile

```

Right now it outputs 
```

$_input
results,from,db2

```

I would like
```

$_input,results,from,db2

```

TIA.

---

### Post by sisco311 on 2010-01-13
```
echo -n whatever >> file
```

---

### Post by prem1er on 2010-01-13
Sorry, I missed this in the echo man pages. -n will echo without a new line

```

   if [ "$_input" != "$_temp" ]; then
      echo -n "$_input, " >> $_dataFile
   fi

   db2 -x "select statement" | sed 's/  */,/g' >> $_dataFile

```

---

