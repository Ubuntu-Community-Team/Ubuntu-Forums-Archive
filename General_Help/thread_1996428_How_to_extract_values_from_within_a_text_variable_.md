---
title: "How to extract values from within a text variable in bash scripts"
date: 2012-06-04
forum: General Help
---

### Post by legolas_w on 2012-06-04
Hi,

I have the following text in a bash variable

```

     [books]    [unavailable] Total books unavailable: 293, borrowed: 273, unknown: 20

```

What I need is to extract those numbers into 3 separate variables. I am using bash and awk is available in the path as well as perl.

Thanks.

---

### Post by cortman on 2012-06-04
Echo the variable and direct the output to awk- you can grab individual groups of characters, usually delineated by a whitespace, as "columns" with awk.

```
echo $books > awk '{ print $5 }'
```

would print "293," (the fifth column).

---

### Post by Vaphell on 2012-06-04
```
$ read -r a1 a2 a3 <<< $(echo ${books//:/,} | awk -F"," '{ print $2, $4, $6 }')
$ echo $a1 $a2 $a3
293 273 20
```
replace ':' -> ',' in text and use ',' in awk as a delimiter. fields 2, 4, 6 are what you need, read them into variables.

---

### Post by sisco311 on 2012-06-04
POSIX shell:
```

unavailable="${books##*unavailable: }"
unavailable="${unavailable%%,*}"

borrowed="${books##*borrowed: }"
borrowed="${borrowed%%,*}"

unknown="${books##*unknown: }"

printf '%s\n' "$unavailable" "$borrowed" "$unknown"

```

BASH array:
```

array=(${books//[!0-9]/ })
printf '%s\n' "${array[@]}"

```

BASH variables:
```
read unavailable borrowed unknown <<< "${books//[!0-9]/ }"
printf '%s\n' "$unavailable" "$borrowed" "$unknown"
```

---

### Post by legolas_w on 2012-06-04
Thank you for all replies. The machine does not have the read command installed so I need to use the awk command with a little change, instead of > we should use |.

> **cortman said:**
> Echo the variable and direct the output to awk- you can grab individual groups of characters, usually delineated by a whitespace, as "columns" with awk.

```
echo $books > awk '{ print $5 }'
```

would print "293," (the fifth column).


How can I avoid getting the , with the number?

Thanks.

---

### Post by sisco311 on 2012-06-04
read is a standard command. It must work in any [posix]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html") shell.

---

### Post by Vaphell on 2012-06-04
> How can I avoid getting the , with the number?

by treating ',' as field delimiter ( -F',' ) just like in my example, before redirecting to *read* via <<<

---

### Post by legolas_w on 2012-06-04
> **sisco311 said:**
> read is a standard command. It must work in any [posix]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html") shell.

Unfortunately it seems that csh does not have the read command. At least it does not work for me.
```

read: Command not found.

```

Thanks.

---

### Post by sisco311 on 2012-06-05
Oh, I see. You are using csh. I was trying to avoid using external tools, but I'm not familiar with csh, so... 

awk is very powerful. This can be solved in different ways. I'd replace each non-digit character with a space and put the remaining numbers in an array.

csh and awk:
```

set bks=( `echo "$books" | awk '{gsub(/[^0-9]/, " "); print}'` )
echo "$bks[1]"
echo "$bks[2]"
echo "$bks[3]"
```

tr would be a better choice if it's available:
```
set bks=( `echo "$books" | tr '[\000-\057\072-\177]' ' '` )
echo "$bks"
```

---

