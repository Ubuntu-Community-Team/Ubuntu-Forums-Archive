---
title: "How to enter many variables into a bash script?"
date: 2012-01-05
forum: General Help
---

### Post by ron999 on 2012-01-05
Hi
If I have a script like this:-

```
#!/bin/bash
sentence=$1" "$2" "$3
echo $sentence
```

I run it like this:-
```
./script.sh the black cat
```

It gives the correct output:- **the black cat**

But, what if the sentence doesn't always contain three words.
What method could be used if the number of words in the sentence changes each time?

---

### Post by Lars Noodén on 2012-01-05
The variable you are probably looking for is [font=Courier New]$@[/font]

It's buried deep down in the manual for [bash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/bash.1.html) where you can find it only if you already know it exists. ;)

---

### Post by WorMzy on 2012-01-05
Hm, this sounds a lot like a homework assignment, so I won't do the work for you. Instead, I'll just suggest that you take the $@ variable that Lars told you about (read up about it in the man pages), and use a foreach loop to create $sentence, instead of explicitly stating each parameter.

---

### Post by ron999 on 2012-01-05
> **Lars Noodén said:**
> The variable you are probably looking for is [font=Courier New]$@[/font]


Thanks Lars:D
```
#!/bin/bash
sentence=$@
echo $sentence
```

---

### Post by Lars Noodén on 2012-01-05
I hope it wasn't homework.  

Do take a few minutes though and find the variable in the man page.  You'll find a lot of cool stuff on the way that you might find useful later.

---

### Post by WorMzy on 2012-01-05
Haha, you might as well just use echo from the start if you're going to do that. At least in a loop you can mix things up a bit. :P


I guess your example was just to demonstrate that you wanted to know about the $@ variable?

---

### Post by ron999 on 2012-01-05
Hello again.
I've hit a problem.
Some of the words in the input sentence have double quotes.
So if the command is this:-
```
./script.sh the "black" cat "again"
```
It gives a return:- **the black cat again**
The quotes are stripped away.:confused:
Google shows it's not so simple ---> [http://stackoverflow.com/questions/3260920/preserving-quotes-in-bash-function-parameters]("http://stackoverflow.com/questions/3260920/preserving-quotes-in-bash-function-parameters")

The result is good if I escape all those double quotes:-
```
./script.sh the \"black\" cat \"again\"
```
Maybe I will run the sentence through a text editor first, find and replace **""** by **\""**
Also ampersand &, replace **&** by **\&**

---

### Post by Dangertux on 2012-01-05
You might also want to look into arrays

[http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

Not that it directly fixes your problem, but it can give you some interesting ways of doing things you might not have thought of yet.

---

