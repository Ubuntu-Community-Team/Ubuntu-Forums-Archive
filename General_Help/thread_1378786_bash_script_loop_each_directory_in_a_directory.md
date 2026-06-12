---
title: "bash script loop each directory in a directory"
date: 2010-01-11
forum: General Help
---

### Post by readycarpenter on 2010-01-11
im new to bash scripting but used to do alot of ahk scripting in windows, im trying loop each directory in a directory, should be something like this... but i just get the indir

```
#!/bin/bash
indir="/media/MaxtorOneTouchIII/Audiobooks"

for bookdir in "$indir"
do
   echo "$bookdir"
done
#End of File
```

---

### Post by Johnny B on 2010-01-11
find /media/MaxtorOneTouchIII/Audiobooks -type d -maxdepth 10

---

### Post by readycarpenter on 2010-01-11
find /media/MaxtorOneTouchIII/Audiobooks -type d -maxdepth 10 
sure that gives me a list, i could also just ls, but i want each directory as a variable for commands within the loop
I found this to work using "$indir"/*
```
#!/bin/bash
indir="/media/MaxtorOneTouchIII/Audiobooks/Robert Jordan"

for bookdir in "$indir"/*
do
  echo "$bookdir"
done
#End of File
```

I'm sure there is an easy way to use ls and grep, does anyone have an example

---

### Post by john newbuntu on 2010-01-11
#!/bin/bash

indir="/home/<usrid>/<somedir>"

IFS='
'
for i in `ls ${indir}`;
do
   echo $i
done

Edit; note the use of backquote and single quotes

---

### Post by colsandurz on 2010-01-12
Ahhh.  I've been looking for a way to do this for a while.  Does anyone know how do to this with python?

---

### Post by kaibob on 2010-01-12
> **readycarpenter said:**
> find /media/MaxtorOneTouchIII/Audiobooks -type d -maxdepth 10 
sure that gives me a list, i could also just ls, but i want each directory as a variable for commands within the loop
<snip>
I fou

There are many ways to do what you want. The one that I would use is included below. It has the advantage that it works with directories with spaces and--more importantly in your case--returns directories but not files. 

```
#!/bin/bash

indir="/media/MaxtorOneTouchIII/Audiobooks/Robert Jordan"

find "$indir" -type d | while read dir ; do
  echo "$dir"
done
```

The above acts recursively. If that's not your desire, just add the -maxdepth find option and set it to 1. You may also want to use the -mindepth option if you want to exclude the parent directory.

---

### Post by readycarpenter on 2010-01-12
> **john newbuntu said:**
> #!/bin/bash

indir="/home/<usrid>/<somedir>"

IFS='
'
for i in `ls ${indir}`;
do
   echo $i
done

Edit; note the use of backquote and single quotes

could you explain the...
IFS='
'

---

