---
title: "bash script variable combinations"
date: 2011-07-23
forum: General Help
---

### Post by maclenin on 2011-07-23
Any insights on how I might achieve the following?

```
#!/bin/bash

f1=apple
f2=banana
f3=grape

echo "Enter number 1,2 or 3:" # 3 is entered

read x

choice=${f+$x} # yielding choice=$f3

echo "$choice" # so $choice is, essentially, read as f3, which = grape

grape
```

I am, essentially, trying to combine "f" and the number entered (3, for example) to create "f3", which when echoed as "$choice" will lead to grape!

Thanks for any suggestions.

---

### Post by mikejonesey on 2011-07-23
```

choices=("f1" "f2" "f3")
read userChoice
((userChoice--))
echo ${choices[userChoice]}

```

---

### Post by zero2xiii on 2011-07-23
Hay,

Why dont you just do:
```
Read option
choice="f$option"

```


this should yeild the desired result....

edit:
 echo of $choice then just gives you f3 (as in your example). changing it to: 

```
Read option
choice="$""f$option"

```

gives on echo of $choice the result $f3 (as in your example), but it doesnt translate the $f3 to the setted value of grape...

edit2:

I asume this is just a VERY simple application program example you gave us, but try this, it might work, might not. It's not pretty, but it works pretty well in my scripts I use this method:

```
 
#!/bin/bash

function fun_1(){
	echo "apple"
}

function fun_2(){
	echo "banana"
}

function fun_3(){
	echo "grape"
}
	
echo "Enter number 1,2 or 3:" # 3 is entered

read option
choice="fun_$option"
$choice	


```

---

### Post by mikejonesey on 2011-07-23
> **zero2xiii said:**
> Hay,

Why dont you just do:

```
Read option
choice="f$option"

```this should yeild the desired result....

because op wants more complex options than f; i was misleading with my f's aploigies;

```
choices=("apple" "banana" "grape")
read userChoice
((userChoice--))
echo ${choices[userChoice]}
```

a simplification could be;
```

choice=("apple" "banana" "grape")
echo ${choice[$(read; ((REPLY--)); echo $REPLY)]}

```

:)

---

### Post by zero2xiii on 2011-07-23
haha... 

Damn..  You use the word "simplification" and thats your simplified verions :confused: hahahaha.. now i remember why im not good at this stuff.. lolz.. 

That works though, seems like I am going to need to get some better bash scripting guides... I haven't even come CLOSE that that level of coding.. GJ

---

### Post by mikejonesey on 2011-07-23
> **zero2xiii said:**
> haha... 

Damn..  You use the word "simplification" and thats your simplified verions :confused: hahahaha.. now i remember why im not good at this stuff.. lolz.. 

That works though, seems like I am going to need to get some better bash scripting guides... I haven't even come CLOSE that that level of coding.. GJ

my fav bash book [http://www.amazon.co.uk/Mastering-Unix-Shell-Scripting-Administrators/dp/0470183012/ref=sr_1_2?ie=UTF8&qid=1311452552&sr=8-2](http://www.amazon.co.uk/Mastering-Unix-Shell-Scripting-Administrators/dp/0470183012/ref=sr_1_2?ie=UTF8&qid=1311452552&sr=8-2) :)

---

### Post by maclenin on 2011-07-24
Thanks folks (and **Totoro**) for your suggestions...after a bit more searching, [**[COLOR="DarkOrange"]_this nugget_[/COLOR]**]("http://www.unix.com/unix-dummies-questions-answers/45589-bash-bad-substitution-problem-pls-help.html") seemed to (re)solve my problem:

```
#!/bin/bash

f1=apple
f2=banana
f3=grape

echo "Enter number 1,2 or 3:" # 3 is entered

read x

choice=f$x # or f${x}

echo **[COLOR="DarkOrange"]${!choice}[/COLOR]** # or "${!choice}"

grape
```

Great to have found a solution (which allowed me to "re-build" the original declared variable (f3, for example) and preserve its original value - grape), but I would like to understand how the **[COLOR="DarkOrange"]![/COLOR]** inside the ${} produces my sought-after result!

Glad it works, however, if someone could clarify, "Why?", 'twould be icing (on the grape)!

---

### Post by Vaphell on 2011-07-24
[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion)

> If the first character of parameter is an exclamation point (!), a level of variable indirection is introduced. Bash uses the value of the variable formed from the rest of parameter as the name of the variable; this variable is then expanded and that value is used in the rest of the substitution, rather than the value of parameter itself. This is known as indirect expansion.

---

### Post by maclenin on 2011-07-25
Thanks, **Vaphell**, for the answer and the reference!

---

