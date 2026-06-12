---
title: "shell programing help !"
date: 2010-01-06
forum: General Help
---

### Post by SaxonC on 2010-01-06
Hi all 
I am new to ubuntu, was trying shell programing just now.
this is what i wrote 
# !/bin/bash
let s=0
for (( i=1; i<=100; i=i+1 ))
do
    s=s+i
done
echo " the result is $s "
# end
the reusult should be 5050 
but what i got is  s=s+i

any ideal ?  
Help would be appreciated !

---

### Post by StuartN on 2010-01-06
> **SaxonC said:**
> this is what i wrote

What you wrote would work, bar some Bash syntax changes. The value of a variable is referenced with a $, e.g. $s. Arithmetic is enclosed in square brackets, e.g. $[$s++]. This works:
```
# !/bin/bash
s=0
for (( i=1; i<=100; i=i+1 )); do
  s=$[$s+$i]
done
echo "The result is $s"
```
Bash syntax is a collection of unrelated conventions, and not very consistent.

Try [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-10.html#ss10.2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-10.html#ss10.2) or search for something like "bash examples" for more.

---

### Post by John Bean on 2010-01-06
> **StuartN said:**
> Bash syntax is a collection of unrelated conventions, and not very consistent.

Indeed. The ability to do the same thing in many ways is both a strength and a weakness - and of course the source of much confusion to newcomers. As an example, this is closer to how I would have coded it in a shell script even though I'm an experienced C programmer very familiar with the C-style for loop:
```

# !/bin/bash
s=0
for i in {1..100} ; do
  s=$[$s+$i]
done
echo "The result is $s"

```
:-)

---

### Post by ghostdog74 on 2010-01-06
> **SaxonC said:**
> Hi all 
I am new to ubuntu, was trying shell programing just now.
this is what i wrote 
# !/bin/bash
let s=0
for (( i=1; i<=100; i=i+1 ))
do
    s=s+i
done
echo " the result is $s "
# end
the reusult should be 5050 
but what i got is  s=s+i

any ideal ?  
Help would be appreciated !

it should be
```

s=$((s+i))

```

---

