---
title: "What's wrong with my code?"
date: 2012-05-26
forum: General Help
---

### Post by hugh_bristol on 2012-05-26
Hi

Really sorry to bother but if anyone can help that would be amazing. I am trying to learn bash programming and functions, and so I have written a simple celcius/farenheit converter. But it doesn't work for some reason - even though all the echo to bc commmands work just fine in the terminal with the same syntax.

```

#!/bin/bash

VAR1=9
VAR2=5
VAR3=32


cel2far ()
{
read -p "enter number in C followed by <ENTER> ==> " resp
part1=echo "scale=2;$VAR1 / $VAR2" | bc
part2=echo "scale=2;$part1 * $resp" | bc
answer_c2f=echo "scale2;$part2 + $VAR3" | bc
echo "$answer_c2f"
}

far2cel ()
{
read -p "enter number in F followed by <ENTER> ==> " resp
part1=echo "scale=5;$resp - $VAR3" | bc
part2=echo "scale=5;$VAR2 * $VAR1" | bc
answer_f2c=echo "scale=2;$part2 * $part1" | bc
echo "$answer_f2c"
}

echo "Is your temperature in celsius or farenheit [C/F]?"

read temp_type

if [ $temp_type == C ]; then
     cel2far
elif [ $temp_type == F ]; then
     far2cel
else echo "unrecognized temp format; please type either C or F [caps]"
fi

```

---

### Post by Habitual on 2012-05-26
maybe quote $resp? ie. "$resp"....?

---

### Post by hugh_bristol on 2012-05-26
Hi

Thank you for your reply - unfortunately it did not work. Here is the output to the terminal when I run the script (it's called testin):


hugh@computer:~/Documents/Code$ ./testin 
Is your temperature in celsius or farenheit [C/F]?
C
enter number in C followed by <ENTER> ==> 44
./testin: line 11: scale=2;9 / 5: No such file or directory
./testin: line 12: scale=2; * 44: command not found
./testin: line 13: scale2; + 32: command not found

---

### Post by sisco311 on 2012-05-26
If you wan't to assign the output of a command or pipeline to a variable, then you have to use command substitution:
```
part1=$(bc <<< "scale=2;$VAR1 / $VAR2")
```

EDIT:
See what I did there? I used a here string instead of a pipeline. ;)

Your method should also work:
```
part1=$(echo "scale=2;$VAR1 / $VAR2" | bc)
```

---

### Post by hugh_bristol on 2012-05-26
That works perfectly, thank you. Don't suppose you could briefly tell me what it is doing?

Hugh

p.s. how do I mark as solved, (and also how do I quote code like you did?)

---

### Post by sisco311 on 2012-05-26
> **hugh_bristol said:**
> That works perfectly, thank you. Don't suppose you could briefly tell me what it is doing?

Hugh


[http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)

> **hugh_bristol said:**
> 
p.s. how do I mark as solved, 


At the top of the page click Thread Tools -> Mark this thread as solved

> **hugh_bristol said:**
> 
(and also how do I quote code like you did?)


[noparse]```
your code her
```[/noparse]

---

### Post by hugh_bristol on 2012-05-26
Thank you for all your help!

---

### Post by sisco311 on 2012-05-26
> **hugh_bristol said:**
> Thank you for all your help!

You are welcome!

---

