---
title: "Bash script - how do I modify varible data with another varible?"
date: 2010-01-31
forum: General Help
---

### Post by bakegoodz on 2010-01-31
I'm building a bash script with the help of the book I bought. I can't find the syntax to accomplish one part of it. I have a variable "part" that is always 4 characters, three letters and one number at the end, example sda1 (yes it is a hard drive). I want the take the number and add it to another variable with just 3 letters. For example take variable "target" with data sdb and modify it to be sdb1, with the number from variable "part"
what is a simple way to express this in bash syntax?

---

### Post by howlingmadhowie on 2010-01-31
> **bakegoodz said:**
> I'm building a bash script with the help of the book I bought. I can't find the syntax to accomplish one part of it. I have a variable "part" that is always 4 characters, three letters and one number at the end, example sda1 (yes it is a hard drive). I want the take the number and add it to another variable with just 3 letters. For example take variable "target" with data sdb and modify it to be sdb1, with the number from variable "part"
what is a simple way to express this in bash syntax?

target=$target`echo $part | cut -c4`

---

### Post by chewearn on 2010-01-31
```

a=sda1
b=sdb

b="$b"`echo "$a" | cut -c4`

```

EDIT:
Opps, late.

---

### Post by ibuclaw on 2010-01-31
You'll be better off using sh's built-in substr function.
```

A=sda1
B=sdb

B=$B${A:3}

```

edit:
To elaborate briefly on how it works (using an example case).
```

test=abcdefghijklmnop

echo ${test}     [COLOR="Blue"]# abcdefghijklmnop[/COLOR]
echo ${test:1}   [COLOR="blue"]# bcdefghijklmnop[/COLOR]
echo ${test:3}   [COLOR="blue"]# defghijklmnop[/COLOR]
echo ${test:7}   [COLOR="blue"]# hijklmnop[/COLOR]
echo ${test: -1} [COLOR="blue"]# p[/COLOR]
echo ${test: -3} [COLOR="blue"]# nop[/COLOR]
echo ${test: -7} [COLOR="blue"]# jklmnop[/COLOR]

```

Regards
Iain

---

### Post by howlingmadhowie on 2010-01-31
an interesting page on string manipulation in bash:
[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

---

### Post by bakegoodz on 2010-01-31
Thanks for your help. One more question, I need the opposite too, take variable data like sda1 and remove the 1, so it is only sda.

I'm looking at this page, but I can't quite figure out the right syntax. 
[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

---

### Post by kaibob on 2010-01-31
> **bakegoodz said:**
> Thanks for your help. One more question, I need the opposite too, take variable data like sda1 and remove the 1, so it is only sda

To continue with tinivole's post, you can do this as shown below. The 0 is position and the 3 is length. 

> $ test=sda1 ; echo ${test:0:3}
sda

Another method is to remove the last character from the string:

> $ test=sda1 ; echo ${test%?}
sda

---

### Post by bakegoodz on 2010-01-31
I tested it out and this is my result, what am I doing wrong?

part=sda1; drive='echo ${part:0:3}'
echo $drive
echo ${part:0:3}

---

### Post by t4thfavor on 2010-01-31
I wrote that into a script I called test.sh

```

#!/bin/bash
part=sda1; drive='echo ${part:0:3}'
echo $drive
echo ${part:0:3}

```

then when I run it I get 
sda

So it's correct for getting the characters from position 0 to 3.

Oh, and you didn't post any results.

---

### Post by kaibob on 2010-01-31
> **bakegoodz said:**
> I tested it out and this is my result, what am I doing wrong?

part=sda1; drive='echo ${part:0:3}'
echo $drive
echo ${part:0:3}

If the goal is to get the string sda into the variable named drive, then you do not need to use the echo command or command substitution.

> $ part=sda1; drive=${part:0:3} ; echo $drive
sda

Perhaps I don't understand what you are trying to do.

---

### Post by bakegoodz on 2010-01-31
drive=${part:0:3}

test:
part=sda1; drive=${part:0:3}
echo $drive

result: sda


Thanks everyone!

---

