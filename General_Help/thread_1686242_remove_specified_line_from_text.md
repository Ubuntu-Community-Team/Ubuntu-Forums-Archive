---
title: "remove specified line from text"
date: 2011-02-12
forum: General Help
---

### Post by spammer-[APTX4869] on 2011-02-12
hi, I wish to move a specified line from a text file:
> 

ltoremove=5 #remove 5th line
i=1
while read line ; do
if [ $i == $ltoremove ] ; then
...
i=$(($i+1))
done < "txt.txt"

how should this actually be done? is there a shorter faster way to do this? 
Thanks,
Ted

---

### Post by Vaphell on 2011-02-12
```
awk 'NR!=5 { print $0 }' txt.txt
```

for any record (by default record=line) with number not equal to 5 print record

---

### Post by dcstar on 2011-02-12
> **Vaphell said:**
> ```
awk 'NR!=5 { print $0 }' txt.txt
```

for any record (by default record=line) with number not equal to 5 print record

Is it school assignment time already?

It must be since these forums are now getting these "requests" from new posters.

Aren't these people supposed to figure out these things for **themselves?**

---

### Post by spammer-[APTX4869] on 2011-02-12
> **Vaphell said:**
> ```
awk 'NR!=5 { print $0 }' txt.txt
```

for any record (by default record=line) with number not equal to 5 print record
Thanks

---

