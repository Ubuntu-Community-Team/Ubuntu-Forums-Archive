---
title: "Bash, Sed and Arrays"
date: 2010-12-22
forum: General Help
---

### Post by ks07 on 2010-12-22
Hey guys,

I'm playing with bash scripts atm, and I'm stuck. I've got an array of names called $NAMES and I have a text file containing the line '#names go here'. How do I replace that line with the contents of $NAMES? 
Better example:
```
echo ${NAMES[@]}
bob joe bill alice
---
cat test.txt
[random text]
#names go here
[random text]

```I've tried using this, but it gives an error message:
```
$ cat test.txt | sed s/"# names go here"/${TEST[@]}/g
sed: -e expression #1, char 11: unterminated `s' command
```Also, once I get this working, I presume the names will all be on one line. Is there any way to get the names printed on a line of their own? The desired output would be:
```
[random text]
bob
joe
bill
alice
[random text]
```Any takers? :popcorn:

---

### Post by Crusty Old Fart on 2010-12-23
> **ks07 said:**
> Hey guys,

I'm playing with bash scripts atm, and I'm stuck. I've got an array of names called $NAMES and I have a text file containing the line '#names go here'. How do I replace that line with the contents of $NAMES? 
Better example:
```
echo ${NAMES[@]}
bob joe bill alice
---
cat test.txt
[random text]
#names go here
[random text]

```I've tried using this, but it gives an error message:
```
$ cat test.txt | sed s/"# names go here"/${TEST[@]}/g
sed: -e expression #1, char 11: unterminated `s' command
```
Well...this works:
```

#!/bin/bash
declare -a names=(bob joe bill alice)
sed s/"#names go here"/"${names
[*]}"/g test.txt
exit 0

```> **ks07 said:**
> 
Also, once I get this working, I presume the names will all be on one line. Is there any way to get the names printed on a line of their own? The desired output would be:
```
[random text]
bob
joe
bill
alice
[random text]
```Any takers? :popcorn:
...and so does this:
```

#!/bin/bash
declare -a names=(bob joe bill alice)
for (( i = 0 ; i < ${#names[@]} ; i++ )); do
  if [[ $i == $(( ${#names[@]} - 1 )) ]]; then
    newnames[$i]=${names[$i]}
  else
    newnames[$i]=${names[$i]}\\n
  fi
done
sed s/"#names go here"/$(echo ${newnames
[*]} | sed 's/ //g')/g test.txt
exit 0

```Merry Christmas,

Crusty

---

