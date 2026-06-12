---
title: "bash only increments up to 2 if I tell it to go up to 100, 10 101 or 10101"
date: 2009-11-07
forum: General Help
---

### Post by rootless on 2009-11-07
Hey, forgive me, I know, I'm working on learning perl, but until then, I'm stuck writing shoddy bash scripts. I'm trying to concatenate random numbers into a user-specified file, a user-specified number of times.

The script works like a charm, unless maxcount is equal to a number with a zero in it. If maxcount is equal to 10, the script only outputs 2 random numbers. I thought bash was reading 10 as binary, but 101 also produces 2, as does 10101, or 100.

Obviously I fail at programming. Can someone help a beginner with a simple problem?

```
#! /bin/bash

RANDOM=$$

echo "How many random numbers do you want?"
read -e maxcount

#declare -i maxcount (tried this it doesn't work)

echo "where is your text file?"
read -e fileinput

while [[ $count < $maxcount ]]
do

let number=$RANDOM%999 ; 

echo $number >> $fileinput

count=$(($count+1))

done

```

---

### Post by kaibob on 2009-11-08
It works if you change the following line:

```
while [[ $count -lt $maxcount ]]
```

I believe < is used with strings while -lt is used with integers.

---

### Post by rootless on 2009-11-08
Aaaah, subtle... bash assumed it was reading a string because of <

Thanks!

---

