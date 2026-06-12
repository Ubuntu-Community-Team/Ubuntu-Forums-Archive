---
title: "Use awk to rearrange datafile content"
date: 2012-07-30
forum: General Help
---

### Post by sd@ksu on 2012-07-30
I have a datafile with contents arranged in three columns separated by space. Here is the content say (**filename:in**):
```

-2 15 101
-1 15 99
0 15 132
1 15 101
2 15 131
-2 10 111
-1 10 79
0 10 142
1 10 151
2 10 121
-2 -15 109
-1 -15 98
0 -15 133
1 -15 108
2 -15 139

```

As you can see, the 1st column has numbers going from -2 to 2 in steps of 1 (5 lines). For each of this, 2nd column's value is fixed at 15, 10 or -15 after each 5 line interval. The 3rd column is my data. This is actually like a x, y, z data. Now I want the data to be rearranged like this (**filename: out**):
```

-2 15 101
-2 10 111
-2 -15 109
-1 15 99
-1 10 79
-1 -15 98
0 15 132
0 10 142
0 -15 133
1 15 101
1 10 151
1 -15 108
2 15 131
2 10 121
2 -15 139

```
..............
i.e., I want to group them w.r.t 1st column values now, instead of the 2nd column values. I think 'awk' is the best option as there is a regular pattern in what I want to do. I can take data from the input file, use the NR option in awk to select my 1st line as:
```

awk 'NR<=1 && NR>=1 { print $1, $2, $3 }' $INPUTFILE > $OUTPUTFILE

```
But two things not obvious to me:
1) How to loop in using NR=a-variable in awk (instead of giving the  numerical value 1 directly to awk, how do I pass as a variable)?
2) How to make it append instead of overwriting the output?
Please help.

---

### Post by steeldriver on 2012-07-30
wouldn't 'sort' be easier?

```
sort -n *file*
```or if you want to order the second column as well (primary k = col 1, secondary key = col 2)
```
sort -k1n -k2n *file*
```

---

### Post by sd@ksu on 2012-07-30
Wonderful..Thanks a lot...I would still keep the thread open as I would also like to have the answer to my above 2 questions: 
1) how to pass a variable in awk?
2) how to append to a file using awk?

---

### Post by Vaphell on 2012-07-30
sort is definitely the right tool for the job here, awk is not really tailored to change the order of data, it specializes more in formatting and extracting required bits.

overwriting is >
appending is >>


> 1) How to loop in using NR=a-variable in awk (instead of giving the numerical value 1 directly to awk, how do I pass as a variable)?

care to explain what you mean exactly?
awk goes line by line and it doesn't make much sense to use NR=variable (in case you plan to go to some earlier line)
in general you simply create a variable and simply use it, eg 
```
BEGIN { line=13; } NR==line { line+=5; }
```
if you want to pass some var from the outside,
```
awk -v var1=value1 -v var2=value2 '...'
```

---

### Post by steeldriver on 2012-07-30
I guess you could do something like

```
for i in {-2..2}; do awk -v arg1=$i '$1==arg1 {print $0;}' *infile*; done > *outfile*
```but like vaphell says, it's not really the right tool for the job... in fact I can almost hear the hounds being released at the mere suggestion...

---

### Post by Vaphell on 2012-07-30
methinks it's a case of 'i only have a hammer and the whole world looks very much like a nail' ;-) been there, done that

---

### Post by sd@ksu on 2012-07-31
Thank you all for the help.
Yes, sort is definitely the right tool. Pardon my ignorance, I am not very skilled at Linux yet. 
I have got the answers I was looking for, so I am marking it as solved. Thanks again. :guitar:

---

