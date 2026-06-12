---
title: "Bash Script Read user input into arrays?"
date: 2010-07-11
forum: General Help
---

### Post by Derrick1978 on 2010-07-11
Hi,

Can someone please tell me if there is a way to store user input in bash script into arrays?

For example,

read 12345 and store it as 1 2 3 4 5 each in a different variable,I've searched and I think what I am looking for is arrays but I wasn't able to find something that takes the user input into arrays. I'm using ```
read var1 var2 var3 var4 var5
``` as a workaround but it needs the user to add a space in between the integers. So it would be best if there is a way to eliminate that.

Lastly, have a nice day everyone!

---

### Post by RHTopics on 2010-07-11
Welcome to Ubuntu Forums.

Here is some Bash code that does what you asked.  As long as each input item is a single digit or character, it will work.  If the length of an input is variable, then a delimiter like a space character is needed to separate the input.

```
#!/bin/bash
echo
echo -n "Enter 5 consecutive digits with each digit between 0 and 9:"
read digits
subscript=0
while [ "$subscript" -lt 6 ]
    do
        digit[${subscript}]=${digits:${subscript}:1 }
        ((subscript +=1))
    done
echo
echo "The third digit is: "${digit[2]}
```

---

### Post by kaibob on 2010-07-11
The shell script by RHTopics works great. See posts 1 and 5 in the following thread for two other bash solutions. 

[http://ubuntuforums.org/showthread.php?t=1456288](http://ubuntuforums.org/showthread.php?t=1456288)

---

### Post by Derrick1978 on 2010-07-11
> **RHTopics said:**
> Welcome to Ubuntu Forums.

Here is some Bash code that does what you asked.  As long as each input item is a single digit or character, it will work.  If the length of an input is variable, then a delimiter like a space character is needed to separate the input.

```
#!/bin/bash
echo
echo -n "Enter 5 consecutive digits with each digit between 0 and 9:"
read digits
subscript=0
while [ "$subscript" -lt 6 ]
    do
        digit[${subscript}]=${digits:${subscript}:1 }
        ((subscript +=1))
    done
echo
echo "The third digit is: "${digit[2]}
```

Hi,
Thanks for the warm welcome, your solution works great! Thanks again.


> **kaibob said:**
> The shell script by RHTopics works great. See posts 1 and 5 in the following thread for two other bash solutions. 

[http://ubuntuforums.org/showthread.php?t=1456288](http://ubuntuforums.org/showthread.php?t=1456288)

Hi,
I have gone through the two solutions, definitely will take them down as well.Thank you.

Have a nice day!

---

### Post by RHTopics on 2010-07-11
You are welcome.  I am glad that code was what you needed.

---

### Post by geirha on 2010-07-11
Reading from stdin is a bit different than reading from a variable like in post 5 in that other thread. Something like this could be used to read a line from stdin into an array of characters:
```
#!/bin/bash

array=() i=0 REPLY=''

printf "String: "
while [[ $REPLY != $'\n' ]]; do
  read -r -n 1 -d ''
  array[i++]=$REPLY
done

echo "${array[@]}"

```

However, the user may get confused if he/she tries to remove the previous char.

---

### Post by kaibob on 2010-07-11
> **geirha said:**
> Reading from stdin is a bit different than reading from a variable like in post 5 in that other thread. <snip>

geirha,

My thought was something similar to:

```
#!/bin/bash

read -p "String: " chars

while read -r -n 1 -d '' ; do
  array[i++]=$REPLY
done <<< $chars

echo "Character 1 is ${array[0]}"

echo "Character 3 is ${array[2]}"
```

---

### Post by geirha on 2010-07-12
> **kaibob said:**
> geirha,

My thought was something similar to:


Yeah, you're right, that's much better. I got carried away; lack of sleep or coffee I guess.

One way to avoid the extra newline added by the <<< btw, is to use process substitution instead.
```
while read...
done < <(printf %s "$chars")

```

---

### Post by kaibob on 2010-07-12
> **geirha said:**
> <snip>One way to avoid the extra newline added by the <<< btw, is to use process substitution instead.
```
while read...
done < <(printf %s "$chars")

```
Thanks for that information. I tried to use a here string once and couldn't get it to work because of the added newline, so this is useful to know.

---

