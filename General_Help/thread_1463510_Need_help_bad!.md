---
title: "Need help bad!"
date: 2010-04-27
forum: General Help
---

### Post by nl4m on 2010-04-27
Lets say that the output of the command "LS" is "File one", "File two", "File3", "File4".

Now if I take the output of the "LS" command and put it through the "For... in" structure, for example:

```
#!/bin/bash
op=$(ls)
for i in $op
do
   echo "$i"
done
```Instead of getting an output of "File one" I get an output of "File" (newline) "one". How do I keep the name of a file together through the "For... in" structure? HELP PLEASE!

---

### Post by dv3500ea on 2010-04-27
use
```
op=*
```
instead of 
```
op=$(ls)
```

---

### Post by nl4m on 2010-04-27
> **dv3500ea said:**
> use
```
op=*
```instead of 
```
op=$(ls)
```

No. I used "LS" as an example. The real code that I am working with has 3 pipes in it. "ls | cut... | grep ... " Now I need THIS output to hold the name of the file through the "For... in" structure.

---

### Post by rnerwein on 2010-04-27
hi
are you looking for something like this.
#!/bin/bash
one_line=""
for i in `ls`
do
        one_line=$one_line$i' '      # build one line - fields are seperated by spaces
        echo $one_line                 # just for fun --> field1 fileld2 ....... 
done
   echo $one_line | nawk ' { print $0 }'  # print out the whole line --> field1 fiield2 .... fieldn

have a look at nawk it's very mighty ( pattern matching, ....... )
ciao

---

