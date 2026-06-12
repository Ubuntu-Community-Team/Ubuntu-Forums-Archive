---
title: "How to find how many times  &quot;something&quot; mentioned in all???"
date: 2010-04-27
forum: General Help
---

### Post by arayici22 on 2010-04-27
Hi all,
 
I downloaded the new kernel and extracted and i was trying to find out 
How many times 'Linus Torvalds' is mentioned in all kernel code related software in newest distribution.
 
can anybody tell me which command to use?????

---

### Post by mcduck on 2010-04-27
Grep will do the job for you:

```
grep -c "string to search" /path/to/somefile
```

---

### Post by arayici22 on 2010-04-27
I tried grep -c "'Linus Torvalds" ./ but didnt find anything?
 
Can i not search all the files instead of one by one?

---

### Post by Dayofswords on 2010-04-27
you want to do recursive ```
grep -Rc "string to search" /path/to/somefile
```

---

### Post by Dayofswords on 2010-04-27
what you could do actually is 
```
grep -R "Linus Torvalds" /to/linux/source/* | wc
```
the output will print 3 numbers

the left number will be how many lines  "Linus Torvalds" appears in. chances are it will only appear a max of once in a line, so thats a good number for how many times its shows up

if you dont care what what case it's in(T or t, L or l, LINUS or linus) add 'i' to '-R' for '-Ri'

---

### Post by arayici22 on 2010-04-27
> **Dayofswords said:**
> what you could do actually is 
```
grep -R "Linus Torvalds" /to/linux/source/* | wc
```
the output will print 3 numbers
 
the left number will be how many lines "Linus Torvalds" appears in. chances are it will only appear a max of once in a line, so thats a good number for how many times its shows up
 
if you dont care what what case it's in(T or t, L or l, LINUS or linus) add 'i' to '-R' for '-Ri'
 
 
Thanks Dayofswords
 that was the i looking for.:P

---

