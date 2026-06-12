---
title: "editing text file through shell script"
date: 2012-02-29
forum: General Help
---

### Post by fra11 on 2012-02-29
Hi!
I need to copy just a certain number of lines from a file to another and I need to do it recursively so I wanted to use a for loop in a shell script.
do you know how can I tell in a shell script something like
copy from line a to line b into file c?
Thanks
:confused:

---

### Post by fra11 on 2012-02-29
Up to now I have tried with something like:

```

#!/bin/bash
file="./angles.ndx"
for ((i=1; i<=2; i++))
#for line in $(cat $file)

do
j=`expr $i + 1`
q=`expr $i + 746`
w=`expr $q + 1`
sed -n -e '$i,${j}p' $file > ./prova_${i}.ndx
#cat $file | n --$j > angles_A_${i}.ndx
#cat -b --$w $file > angles_B_${q}.ndx

done

```

which didn't work.
Any suggestions?
Thanks!!!

---

### Post by matt_symes on 2012-02-29
Hi

Use double quotes and not single quotes around the sed command to allow shell expansion of the variables.

```
sed -n -e **"$i,${j}p"** $file > ./prova_${i}.ndx
```

```
matthew@matthew-Aspire-7540:~$ i=2; j=3; sed -n -e '$i,${j}p' .profile 
,${j}p
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ i=2; j=3; sed -n -e "$i,${j}p" .profile 
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
matthew@matthew-Aspire-7540:~$
```

You never stated what your errors where and where it was failing.

If you're using bash then prefer 

```
j=$(($i + 1));
``` 

over 

```
j=`expr $i + 1`;
```

Might is suggest using semi-colons as well.

Kind regards

---

### Post by fra11 on 2012-02-29
Thanks!
However, my script is still not working.
My code now looks like
```

#!/bin/bash

for ((i=1; i<=2; i++))

file="ang_${i}.xvg"
do
j=$(($i + 1))
echo $j 

sed -n -e "$i,${j}p" $file > ./prova_${i}.ndx

done

```

where $file is my input file and prova_${i}.ndx is my output and I need to copy from line i to line j into the output.
My error message looks like

./edit_file.sh: line 5: syntax error near unexpected token `file="ang_${i}.xvg"'
./edit_file.sh: line 5: `file="ang_${i}.xvg"'

Can you please be so kind to explain to me what am I doing wrong?
Thanks:confused:

---

### Post by Vaphell on 2012-02-29
```
for (( ... ))
do
    <stuff>
done
```

you got
```
for ((i=1; i<=2; i++))

**file="ang_${i}.xvg"**
do
```
what?

consider indenting your code for better readability

trivia not related to the problem at hand:
$ is not necessary inside (( )), any text inside 'integer brackets' is considered as a variable name either way.
It's a difference between pasting the value and then evaluating "(( 1+1 ))" and evaluating "(( i+1 ))" right off the bat. Your for loop does that, so why not j=(())? :-)

---

### Post by fra11 on 2012-02-29
thanks!!!
Any way, can I ask you another question? if I have a file that looks like 

5 10 12 14 1 1 180 30.000000 1 2 
14 20 22 24 1 1 180 30.000000 1 2 
24 29 31 33 1 1 180 30.000000 1 2 
33 38 40 42 1 1 180 30.000000 1 2 
42 47 49 50 1 1 180 30.000000 1 2 
50 54 56 58 1 1 180 30.000000 1 2 
58 63 65 67 1 1 180 30.000000 1 2 
67 71 73 75 1 1 180 30.000000 1 2 


and I want to edit is so that it looks like

5 10 12 14 
14 20 22 24 
24 29 31 33 
33 38 40 42 
42 47 49 50 
50 54 56 58 
58 63 65 67 
67 71 73 75 

s basically selecting the first 4 columns and deleting the rest,
in which way should I change the sed command to point at columns instead of rows? Or do you have better suggestions? I know that awk should help but I'm not sure of the syntax... 
Thanks again :D

---

### Post by Khayyam on 2012-02-29
> **fra11 said:**
> Any way, can I ask you another question? if I have a file that looks like [...] selecting the first 4 columns and deleting the rest, in which way should I change the sed command to point at columns instead of rows? Or do you have better suggestions? I know that awk should help but I'm not sure of the syntax.

fra11 ...

```
awk '{print $1,$2,$3,$4}' input.txt > output.txt
```As for your first question ...

```
awk 'NR==3,NR==4' input.txt > output.txt
```This selects line 3 to line 4 from input.txt ... your input.txt can be any any expression necessary to find your file(s) ..

EDIT: 20 minutes later I'm still giggling at "in which way should I change the sed command to point at columns instead of rows" .. poor me.

HTH ... khay

---

### Post by fra11 on 2012-03-02
Thank you so much! your answer was really helpful.
However I realized that my input file is messed up, in the sense that the columns at a certain point merges so I cannot simply select the 3 columns, but I have to be more specific.
My input file looks like

[RIGHT][LEFT]```


 988LEU      C 9994 -10.285 -16.373  -2.818
[/LEFT]
[/RIGHT]
  988LEU      O 9995 -10.175 -16.392  -2.767
  989ALA      N 9996 -10.393 -16.446  -2.785
  989ALA      H 9997 -10.481 -16.428  -2.828
  989ALA     CA 9998 -10.380 -16.552  -2.689
  989ALA     CB 9999 -10.514 -16.623  -2.660
  989ALA      C10000 -10.285 -16.654  -2.743
  989ALA      O10001 -10.200 -16.706  -2.670
  990ALA      N10002 -10.297 -16.686  -2.873
  990ALA      H10003 -10.366 -16.639  -2.928
  990ALA     CA10004 -10.214 -16.785  -2.936
  990ALA     CB10005 -10.252 -16.810  -3.083


```

and I need something that looks like 

```

 988      C 9994
  988     O 9995
  989     N 9996 
  989     H 9997
  989     CA 9998
  989     CB 9999 
  989     C 10000 
  989      O 10001
  990      N 10002
  990      H 10003
  990     CA 10004
  990     CB 10005


```

Any help on how to do that? Up to now I have tried something like this

```

awk '{print $1 /[0-9]/, $2, $3 /[0-9]/}' $file > column_input.ndx

```

and my error output looks like

```

awk: {print $1 /[0-9]/, $2, $3 /[0-9]/}
awk:            ^ syntax error
awk: {print $1 /[0-9]/, $2, $3 /[0-9]/}
awk:                ^ syntax error
awk: {print $1 /[0-9]/, $2, $3 /[0-9]/}
awk:                                ^ syntax error
awk: {print $1 /[0-9]/, $2, $3 /[0-9]/}
awk:                                  ^ unterminated regexp
awk: cmd. line:1: {print $1 /[0-9]/, $2, $3 /[0-9]/}
awk: cmd. line:1:                                   ^ unexpected newline or end of string

```

Any help?
Thank you so so much:confused:

---

### Post by Vaphell on 2012-03-02
it's very unfortunate that your columns get glued together when 3rd one is 5digits long, that slightly complicates things in straightforward awk approach.

sed way
```
$ echo "988LEU      O 9995 -10.175 -16.392  -2.767
  989ALA      N 9996 -10.393 -16.446  -2.785
  989ALA      H 9997 -10.481 -16.428  -2.828
  989ALA     CA 9998 -10.380 -16.552  -2.689
  989ALA     CB 9999 -10.514 -16.623  -2.660
  989ALA      C10000 -10.285 -16.654  -2.743
  989ALA      O10001 -10.200 -16.706  -2.670
  990ALA      N10002 -10.297 -16.686  -2.873
  990ALA      H10003 -10.366 -16.639  -2.928
  990ALA     CA10004 -10.214 -16.785  -2.936
  990ALA     CB10005 -10.252 -16.810  -3.083" | **sed -r 's/^\s*([A-Z0-9]+)\s*([A-Z]+)\s*([0-9]+)\s.*$/\1 \2 \3/'**
988LEU O 9995
989ALA N 9996
989ALA H 9997
989ALA CA 9998
989ALA CB 9999
989ALA C 10000
989ALA O 10001
990ALA N 10002
990ALA H 10003
990ALA CA 10004
990ALA CB 10005
```

---

### Post by fra11 on 2012-03-02
Thank you so much!:D

---

### Post by aeiah on 2012-03-02
if your data is very consistent, you could just pipe it to:
```

colrm 21
```

but since you have a more robust sed command now, you should probably stick with that :popcorn:
```


[debian ~] cat test
  988LEU      O 9995 -10.175 -16.392  -2.767
  989ALA      N 9996 -10.393 -16.446  -2.785
  989ALA      H 9997 -10.481 -16.428  -2.828
  989ALA     CA 9998 -10.380 -16.552  -2.689
  989ALA     CB 9999 -10.514 -16.623  -2.660
  989ALA      C10000 -10.285 -16.654  -2.743
  989ALA      O10001 -10.200 -16.706  -2.670
  990ALA      N10002 -10.297 -16.686  -2.873
  990ALA      H10003 -10.366 -16.639  -2.928
  990ALA     CA10004 -10.214 -16.785  -2.936
  990ALA     CB10005 -10.252 -16.810  -3.083
[debian ~] cat test | colrm 21
  988LEU      O 9995
  989ALA      N 9996
  989ALA      H 9997
  989ALA     CA 9998
  989ALA     CB 9999
  989ALA      C10000
  989ALA      O10001
  990ALA      N10002
  990ALA      H10003
  990ALA     CA10004
  990ALA     CB10005

```

---

### Post by Khayyam on 2012-03-02
fra11, vaphell, et al ...

I can't believe that something will output tables so inconsistantly ... if colomns are "merged" like this how is program supposed to parse it, the mind boggles.

**If** it were properly tabled then the task would be simple:

```
awk '{print(substr($1,1,3)),$2,$3}' input.txt | column -t > output.txt
```

If "[COLOR=DarkRed]988[/COLOR]LEU" increments, then something the following will be necessary:

```
awk '{print(substr($1,1,length($1 -3))),$2,$3}' input2.txt |column -t > output.txt
```

I would write to the applications authors and ask howtheythinimwo ...

best ... khay

---

### Post by Vaphell on 2012-03-02
i agree that inconsistent data is full of fail and something should be done, no questions about it.


as for the sed solution i suggested, i didn't notice that only digits from the first column should be considered. Fixing it is easy to figure out, replace ([A-Z0-9]+) with ([0-9]+)[A-Z]+

---

