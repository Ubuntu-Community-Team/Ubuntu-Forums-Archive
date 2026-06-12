---
title: "Join complains about file not being in sorted order"
date: 2010-06-10
forum: General Help
---

### Post by duartemolha on 2010-06-10
Hi Guys...

I am not sure if this is the right forum to ask this but I am having a problem with the join command in by ubuntu machine that does not happen when I use a diferent linux computer (running debian).

I have 2 sorted files 1 file with 1 column with names
Another file has the same fist column and additional columns with more data.

I use the join command to obtain a filtered 3 file with the data from the second file filtered by the names on the fist file:

sort file1 > file1_sorted
sort file2 > files2_sorted

join file1_sorted files2_sorted > Filtered_data

eg:

file1_sorted:
a
b
d

file2_sorted
a Data1...
b Data2...
c Data3...
d Data4...

Filtered_data
a Data1...
b Data2...
d Data4...

_________________________

when I do this is my ubuntu machine I get this warning: 

join: file 2 is not in sorted order

and although it does the join command it does not join all the correct required lines

If I do exactly the same procedure on a different linux machine (in this case a machine running debian), the process runs just fine, It does not complain and I get the correctly filtered data.

Has anyone experiences something similar?

Best regards, 

    Duarte

---

