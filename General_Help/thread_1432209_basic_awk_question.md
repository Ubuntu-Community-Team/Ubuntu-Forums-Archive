---
title: "basic awk question"
date: 2010-03-17
forum: General Help
---

### Post by mortalfunk on 2010-03-17
Hi.

I'm trying to use awk in a bash script. The line that is giving me grief is:

```

num=633674
x_orign=3000000.0

x_coordinate=$(awk '{if ($1==num) {print $3}}' file.txt

difference=$(echo $x_origin - $x_coordinate | bc -l)
echo $difference

```

What happens is that I actually have multiple x coordinates that get returned by awk! 

So awk returns:
2691917.0
2691924.5

How can I place both these results into a bash variable? Or into an array, etc?

---

### Post by prodigy_ on 2010-03-17
It's very easy to manipulate arrays in bash. A simple example: ```
#!/bin/bash
ARRAY=( `echo "a1 a2 a3 a4 a5"` )
I=0
while [ $I -le 4 ]
do
  echo ${ARRAY[$I]}
  ((I++))
done
```
This will output elements one by one (a1, a2, etc.)

---

### Post by DaithiF on 2010-03-17
do you need to capture the results in an array, or is it enough to process each result as it is output from awk, e.g.
awk '{if ($1==num) {print $3}}' file.txt | while read result
do
    difference=$(do something with $result here)
    echo $difference
done

---

