---
title: "NEWBIE: if ... then ... else =====&gt; illegal number?"
date: 2011-06-13
forum: General Help
---

### Post by eddie3000 on 2011-06-13
Ok! I guess you've all noticed I'm learning. I'm doing a linux course and I have to do an exercise. I have to write a simple script where the computer asks a question, and the user has to type in "T" for true or "F" for false. The answers are stored in a variable x. At the beginning of the script I assign two variables t="T" ans f="F". I then try:

if [ "$x" -eq "$t" ]
then
    echo "Correct"
else
    echo "Wrong"
fi

But I get an error: "Illegal number : "$x"" (where "$x" is whatever I answer to the question).
What am I wrong about?
I would also appreciate a link to a good tutorial on this subject. I've been googling around for hours and I keep finding slightly different results, some work, others don't, I sometimes get parts of my script going, but then I change something and it doesn't.
Thanks.
Here's the script:

```
c="Correct!"
w="Wrong!"
g="Congratulations, you have passed the test."
b="Sorry. Try again"
a=0
echo "Hello $USER!"
echo "Today is `date`."
echo "Are the following sentences true or false?."
echo "Type T for true and F for false."
echo
read -p "Linux is based on Microsoft Windows.(Type T or F):" n
if [ "$n" -eq "F" ]
then
    a=$(( $a + 1 ))
    echo $c
else
    echo $w
fi
read -p "Linux is great.(V ó F):" n
echo $n
if [ "$n" -eq "$v" ]
then
    a=$(( $a + 1 ))
    echo $c
else 
    echo $m
fi
echo $a
if [ $a -eq 2 ]
then
    echo $g
else
    echo $b
fi
sleep 5
exit

```

---

### Post by nothingspecial on 2011-06-13
Hi,

Bear in mind that we are not supposed to help with homework, but here is a good bash website

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

be sure to read the pitfalls and faq sectiond too.

---

### Post by TeoBigusGeekus on 2011-06-13
To get you started, add
```
#!/bin/bash
```
at the beginning of the script.

---

### Post by eddie3000 on 2011-06-13
Thanks. I am not asking anybody to do my homework. In fact, the exercise is voluntary, and the actual conditions the tutor gave us are very flexible giving us a huge margin for creativity.
The course I'm doing is done on the internet and it's free, and the documentation I have been given isn't all that clear. For instance, ¡t doesn't even point out the importance of spaces here and there in scripting. It's in pdf format and seems to have been written quickly by somebody who assumes you know what he's talking about.
I'm not sure what my problem is, but I think the if command and the variables have to be numbers and not letters. Is that correct?

---

### Post by TeoBigusGeekus on 2011-06-13
First of all, what is the $v variable in your script?

---

### Post by eddie3000 on 2011-06-13
Sorry, that's a type error. It should be t. I quickly translated it into English, as I'm doing the course in Spanish. All variables called v should be t. Just sec, I'll double check all of it and post it again corrected.

---

### Post by nothingspecial on 2011-06-13
Well you've got a number of problems.

Here's a few hints.

-eq between the square brackets expects numbers not letters. You are asking weather or not the answer supplied is a specific letter.

use = instead of -eq

Type ```
man [
``` in your terminal to see which option does which.

---

### Post by eddie3000 on 2011-06-13
```
#!/bin/bash
c="Correct!"
w="Wrong!"
g="Congratulations, you have passed the test."
b="Sorry. Try again."
a=0
f="F"
t="T"
echo "Hello $USER!"
echo "Today is `date`."
echo "Are the following sentences true or false?."
echo "Type T for true and F for false."
echo
read -p "Linux is based on Microsoft Windows.(Type T or F):" n
echo $n
echo $a
if [ "$n" -eq "$f" ]
then
    a=$(( $a + 1 ))
    echo $c
else
    echo $w
fi
echo $a
read -p "Linux is great.(T or F):" n
echo $n
echo $a
if [ "$n" -eq "$t" ]
then
    a=$(( $a + 1 ))
    echo $c
else 
    echo $m
fi
echo $a
if [ $a -eq 2 ]
then
    echo $g
else
    echo $b
fi
sleep 5
exit

```

---

### Post by eddie3000 on 2011-06-13
I dunnow what I've done. It works now:confused:

---

### Post by TeoBigusGeekus on 2011-06-13
> **eddie3000 said:**
> I dunnow what I've done. It works now:confused:

```
#!/bin/bash
```

---

### Post by eddie3000 on 2011-06-13
Thanks for the info guys.

I tried it without #!/bin/bash and it still works (under ubuntu 11.04). I changed all the -eq to =, I think that's what did it. 

I'll be reading through the link nothingspecial posted. It talks about good practice things like the #!/bin/bash TeoBigusGeekus talked about. All good stuff. It's just weird the documentation I was given doesn't seem to mention any of this. 

Thanks very much.

---

