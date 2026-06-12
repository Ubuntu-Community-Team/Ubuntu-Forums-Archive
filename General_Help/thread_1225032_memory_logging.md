---
title: "memory logging"
date: 2009-07-28
forum: General Help
---

### Post by ub007 on 2009-07-28
Hi,

I've written this small script to log memory usage from /proc statm

> while [ 1=1 ]
do 
   date -R >> $2
   cat /proc/$1/statm >> $2
   'sleep' ls
done 

where $1 is the pid of process & $2 is the file it logs to.

The output is 

> Tue, 28 Jul 2009 08:01:35 +0000
3279 1282 851 1806 0 773 0
....
....
....

How can i get it side by side as in 

> Tue, 28 Jul 2009 08:01:35 +0000 3279 1282 851 1806 0 773 0

or even better excluding some fields from the date

[COLOR="DarkRed"]> Tue, 28 Jul 08:01:35 3279 1282 851 1806 0 773 0[/COLOR]

Any ideas???

Cheers
David

---

### Post by DaithiF on 2009-07-28
hi
use variables, as follows:

d=$(date -R)
m=$(cat /proc/$1/statm)

echo "$d $m" >> $2

to change the format of the date, see 
man date

date +"%a %d %b %Y %T" is what you want i think

---

### Post by ub007 on 2009-07-28
Thank you very much.That worked.

> Tue, 28 Jul 08:01:35 3279 1282 851 1806 0 773 0 
...
...
How can I get it to excel format??
 
I tried
cat logfile.txt | awk '{print $1 "\t" $2 "\t" $3 "\t" $4 "\t" $5 "\t" $6 "\t" $7 "\t" $8 "\t" $9}' 

The output is 
[COLOR="Red"]Tue, 28 Jul-----08:01:35[/COLOR]-----[COLOR="Blue"]3279-----1282-----851-----1806-----0-----773-----0[/COLOR] 

I got it right for the values marked in blue,but for the date,i wish that could be together as in the output before the awked command as in


Tue, 28 Jul-08:01:35-----3279-----1282-----851-----1806-----0-----773-----0

---- indicate blank spaces

Any ideas?

David

---

### Post by DaithiF on 2009-07-28
Hi,
You're almost there...
> **ub007 said:**
> I tried
cat logfile.txt | awk '{print $1 "\t" $2 "\t" $3 "\t" $4 "\t" $5 "\t" $6 "\t" $7 "\t" $8 "\t" $9}' 


... just leave out the first "\t" or two in your awk script (depending on how many spaces you have appearing in your preferred date format, so as not to insert tabs between the elements of the date.

Also, your cat & pipe into awk aren't necessary, just let awk do its stuff on logfile directly:
```
awk '{print $1 $2 $3 "\t" $4 "\t" $5 "\t" $6 "\t" $7 "\t" $8 "\t" $9}' logfile

```

---

### Post by ub007 on 2009-07-28
did try that but the output was

> awk '{print $1 $2 "\t" $3 "\t" $4 "\t" $5 "\t" $6 "\t" $7 "\t" $8 "\t" $9}' logfile


Tue, 28 [COLOR="Red"]Jul08[/COLOR]:01:35-----3279-----1282-----851-----1806-----0-----773-----0
Theres no space between the day and time. :(

---

### Post by DaithiF on 2009-07-28
so put in space where you want it:

awk '{print $1 $2 " " $3 "\t" $4 "\t" $5 "\t" $6 "\t" $7 "\t" $8 "\t" $9}' logfile

---

### Post by ub007 on 2009-07-28
perfect..that worked


Was wondering if theres anyway to multiply the values by 4 in each column....cz stam values are in 4k byte pages

Tue, 28 Jul 08:01:35-----3279-----1282-----851-----1806-----0-----773-----0 

> -----3279-----1282-----851-----1806-----0-----773-----0 
wish to multiply each of these vals by 4...:confused:

---

### Post by DaithiF on 2009-07-28
> **ub007 said:**
> perfect..that worked


Was wondering if theres anyway to multiply the values by 4 in each column....cz stam values are in 4k byte pages

Tue, 28 Jul 08:01:35-----3279-----1282-----851-----1806-----0-----773-----0 

 
wish to multiply each of these vals by 4...:confused:

awk can do that, use $n * 4  rather than just $n for the ones you want to multiply

```
awk '{print $1 $2 " " $3 "\t" $4 * 4 "\t" $5 *4 "\t" $6 * 4"\t" $7 * 4 "\t" $8 * 4 "\t" $9 * 4}' logfile 	
```

---

