---
title: "Trying to write script to perform tasks number of times depending on user input"
date: 2011-04-13
forum: General Help
---

### Post by mkarr on 2011-04-13
I'm trying to write a bash script with a for loop that will perform two tasks a number of times depending on the number the user enters at the start. Here is what I got so far. It works fine the first time but then it just exits with no error msgs. The problem is in the way I have written the loop command. I have searched the web for examples to find out what I'm doing wrong with no luck. Any help would be greatly appreciated.




                         
[INDENT][INDENT]#!/bin/bash

declare -i Num=1
declare -i Strnum=8

read -p "Enter the number: " UserNum

for Num in $UserNum
do [INDENT]
	echo $Strnum
	if test  $Strnum == 8
	then
[INDENT]		xmacroplay ":0.0" < TaskOne.txt
		Strnum=0[/INDENT]
	fi
	xmacroplay ":0.0" < TaskTwo.txt
	Strnum=$(( Strnum+1 ))
 	Sleep 75[/INDENT]
done[/INDENT][/INDENT]

---

### Post by WorMzy on 2011-04-13
```
for Num in $UserNum
```

This is the reason why you're only getting one iteration; you're treating UserNum as an array, when it's just a number.

Take a look at this: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html"), in particular, look at the While and Until examples.

---

### Post by DaithiF on 2011-04-13
Hi, the bash for loop does not work the way you think it does.  

take a look at:
man bash | less +/"for name"

there are two types.  You could either do:

```
for (( i=1; i <= $userNum; i++ ))
do
   # do stuff here
done
```

or:

```
for i in $(seq 1 $userNum)
do
   # do stuff here
done 
```

and a variant on the second which avoids calling the external seq command but which will do the wrong thing if userNum is not a valid number is:
```
for i in {1..$userNum}
do
   # do stuff here
done

```

and just in case it isn't clear why your version wasn't working, try these:
```
for i in 5
do
   echo $i
done

```

```
for i in 5 10
do 
  echo $i
done

```

```
for i in is it clear yet
do
   echo $i
done

```

---

### Post by mkarr on 2011-04-13
Excellent help! I think I can use the until loop but now my sleep command isn't pausing for 75 seconds. Do I need to use 75000?

---

