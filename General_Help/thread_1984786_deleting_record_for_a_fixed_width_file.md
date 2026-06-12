---
title: "deleting record for a fixed width file"
date: 2012-05-22
forum: General Help
---

### Post by bujji4you on 2012-05-22
I want to delete the record if I find a word (dd)in the length(5-7). Let's think that (5-7) length is FF2. 
This is a fixed width file. 
ex f1 
ff1 ff2 ff3 
sds dd fd 
sd ss ew 
dd dd se 
o/p should be like 
 
ff1 ff2 ff3 
sd ss ew

---

### Post by steeldriver on 2012-05-22
you can use 'sed'

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

search for 4 characters followed by literal dd and delete the line

or 3 characters followed by whitespace followed by literal dd if your group delimiter is not always just a single space

btw in your example the dd is NOT always at position 5-7 (e.g. 'dd dd se') so you probably need to spend a bit more time specifying EXACTLY what pattern you want to match (is it really fixed width or whitespace delimited?)

---

### Post by bujji4you on 2012-05-23
Thank you for replying. 
Actually, the requirement is something like ...I have all the country details in the length(Ex: 5-7) Lets think DD is country code. Only, thing  I need to do is delete the dd record. 
Could you pls tell, how to write in a script. I am completely new to scripting. 
 
1. Where we need to define the length. So that script will go to that particular length>search>delete the record.
 

ff1 ff2 ff3 
sds dd fd 
sd ss ew 
ee dd se 
 
 
> **steeldriver said:**
> you can use 'sed'
 
[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)
 
search for 4 characters followed by literal dd and delete the line
 
or 3 characters followed by whitespace followed by literal dd if your group delimiter is not always just a single space
 
btw in your example the dd is NOT always at position 5-7 (e.g. 'dd dd se') so you probably need to spend a bit more time specifying EXACTLY what pattern you want to match (is it really fixed width or whitespace delimited?)

---

### Post by bujji4you on 2012-05-23
actual data will be
ads  2111dd 258
saw  2545ss 555
ess  4572dd  265
 
So, in the above ex dd comes in 2col. So, I need to delete the complete record O/p i want to be as 
Its a fixedwidth file. Iet us take ex that dd comes in (7-9)
 
saw  2545ss 555
because it does not have dd.
 
 
 
> **steeldriver said:**
> you can use 'sed'
 
[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)
 
search for 4 characters followed by literal dd and delete the line
 
or 3 characters followed by whitespace followed by literal dd if your group delimiter is not always just a single space
 
btw in your example the dd is NOT always at position 5-7 (e.g. 'dd dd se') so you probably need to spend a bit more time specifying EXACTLY what pattern you want to match (is it really fixed width or whitespace delimited?)

---

### Post by steeldriver on 2012-05-23
I don't think you are getting that space is a character

if your data is EXACTLY as you have typed above, i.e. columns separated (delimited) by spaces (or tabs)

AND

the 2nd column is exactly 4 digits followed by letters

AND 

you want to find where 2nd columns end in dd and delete those lines

THEN

```
sed '/[ \t]*[0-9]\{4\}dd/d' *yourfile* 
```should work

---

### Post by bujji4you on 2012-05-24
Thank you for your promt reply. However,
 
at times the data looks like
 
ss 12dd  ss
es     dd ww 
 
That was the reason i am specific about range. Ex(5-7).
I want the shell to go to that range(5-7)>search for dd> and then delete the complete record. 
 
Kindly, help
 
 
> **steeldriver said:**
> I don't think you are getting that space is a character
 
if your data is EXACTLY as you have typed above, i.e. columns separated (delimited) by spaces (or tabs)
 
AND
 
the 2nd column is exactly 4 digits followed by letters
 
AND 
 
you want to find where 2nd columns end in dd and delete those lines
 
THEN
 
```
sed '/[ \t]*[0-9]\{4\}dd/d' *yourfile* 
```should work

---

### Post by satish_j on 2012-05-24
i have not used sed but i think foll grep command should also work.It should get you a separate file with filtered results:
```

grep -v /dd/ <input file> > newfile

```
Try it & let us know if it works..

---

### Post by bujji4you on 2012-05-24
satish: thx u. however, i need the sheel to go to specific length and find the word dd and then delete the record. 
 
ss   12123dd sds
21   11111dd  dds
In the above ex  dd is placed at 10-11
 
> **satish_j said:**
> i have not used sed but i think foll grep command should also work.It should get you a separate file with filtered results:
```

grep -v /dd/ <input file> > newfile

```
Try it & let us know if it works..

---

### Post by satish_j on 2012-05-24
> **bujji4you said:**
> satish: thx u. however, i need the sheel to go to **specific length** and find the word dd and then delete the record.

What is that specific length?Is the file delimited by tab fields??
In your very first post,the example had the 'dd' string at very 1st place in one of the record..

Edit:-Ok,let me clarify it further.
Do you want to delete those records which contain 'dd' in their 2nd column???I mean,the string 'dd' appears only in 2nd column or it can appear in any column??

---

### Post by codemaniac on 2012-05-24
Something like below

```
awk 'substr($0,5,2) != "dd"{print}' input_file
```

---

### Post by bujji4you on 2012-05-24
Thx u codemaniac. It worked. 
 
could you pls help me in calculating null values in each column. Pls expain using substr
something like
f1= substr($0,1,3)
using any grep, awk, sed.. Dont no how to use. Just suggestion. Hope I am clear. I need null count for specific lenght.
 
ex
f1...f2...f3
a... ...g
b...e....
... . f.....
O/p
Nuill count in f1=1
Nuill count in f2=1
Nuill count in f3=2
How to calculate null values in each column. .
Note: Dots in example is nothing. I just made for the ex so that col data does not merge with each other. 
 
 
 
> **codemaniac said:**
> Something like below
 
```
awk 'substr($0,5,2) != "dd"{print}' input_file
```

---

### Post by codemaniac on 2012-05-24
> **bujji4you said:**
> Thx u codemaniac. However, could u pls tell y u have used print in that line. 
 
also pls help me in writing script. I 
 
#!/usr/bin/bash
f1= path/a.txt
f2= path/b.txt
 
$awk ' substr ($0, 1466, 1468) !="ARM"?' f1 > f2
 
I am getting error.
 
Error: $awk ' substr ($0, 1466, 1468) !="ARC"?' cannot find.
I am completely new to script.

Print would print the current line processed by AWK to the console.
Have you tried $f1 and $f2 instead .
Please note that there should be no spaces in both sides while declaring variables in the script .

---

### Post by bujji4you on 2012-05-25
Thx u. I used $f1 and f2.
 
Could you pls help me in this ex too..
 

Need to calculate null values in each column. Pls explain using substr
something like
f1= substr($0,1,3)
using any grep, awk, sed.. Dont no how to use. Just suggestion. Hope I am clear. I need null count for specific lenght.

ex
f1...f2...f3
a... ...g
b...e....
... . f.....
O/p
Nuill count in f1=1
Nuill count in f2=1
Nuill count in f3=2
How to calculate null values in each column. .
Note: Dots in example is nothing. I just made for the ex so that col data does not merge with each other. 


> **codemaniac said:**
> Print would print the current line processed by AWK to the console.
Have you tried $f1 and $f2 instead .
Please note that there should be no spaces in both sides while declaring variables in the script .

---

