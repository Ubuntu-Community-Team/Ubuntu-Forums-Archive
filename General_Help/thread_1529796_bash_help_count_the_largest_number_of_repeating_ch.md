---
title: "bash help: count the largest number of repeating characters"
date: 2010-07-12
forum: General Help
---

### Post by lethalfang on 2010-07-12
Hi guys, I'm trying to find a script that will return me the largest number of repeating characters.
Say, I have the following line in a text file:

12345AAAAA6789AAA

I want it to return 5, because "A" is repeated 5 times in this line (more than 3 at the end). 

Thanks.

---

### Post by geirha on 2010-07-12
Bash is not the right tool for the job, though it's possible. I'd recommend python or ruby or some other easy scripting language.

Shall it look for a specific character (e.g. A), or just the longest sequence of any character?

---

### Post by lethalfang on 2010-07-12
> **geirha said:**
> Bash is not the right tool for the job, though it's possible. I'd recommend python or ruby or some other easy scripting language.

Shall it look for a specific character (e.g. A), or just the longest sequence of any character?


Yeah, I'm kinda looking for a one- or two-liner to do the job..... don't know if it's possible.
I am just looking for one specific repeating character (e.g. A).

---

### Post by geirha on 2010-07-12
Awk came to mind. 

```
string=12345AAAAA6789AAA char=A
awk -v re="$char+" '{s=$0; while (match(s,re)) {if (RLENGTH>max) max=RLENGTH; s=substr(s, RSTART+RLENGTH);}} END{print max}' <<< "$string"
```

---

### Post by lethalfang on 2010-07-12
> **geirha said:**
> Awk came to mind. 

```
string=12345AAAAA6789AAA char=A
awk -v re="$char+" '{s=$0; while (match(s,re)) {if (RLENGTH>max) max=RLENGTH; s=substr(s, RSTART+RLENGTH);}} END{print max}' <<< "$string"
```

Thanks. You've saved me many hours of ugly codings. :p

---

### Post by renkinjutsu on 2010-07-12
oops..
lol problem already solved

---

### Post by kaibob on 2010-07-12
Geirha's solution is best, but I wanted to give this a try with bash.  

```
#!/bin/bash

str=12345AAAAA6789AAA
char=A
num=0

arr=( ${str//[!${char}]/ } )

for i in ${!arr[@]} ; do
  [ "${#arr[$i]}" -gt "$num" ] && num=${#arr[$i]}
done

echo "There are $num consecutive ${char}'s"
```

---

