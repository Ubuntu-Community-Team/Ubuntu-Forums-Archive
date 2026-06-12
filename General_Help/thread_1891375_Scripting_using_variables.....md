---
title: "Scripting using variables...."
date: 2011-12-05
forum: General Help
---

### Post by Spyderkid on 2011-12-05
I've been trying to make this simple script which uses variables

but it doesn't seem to work :S

any help?
```
#!/bin/bash

red=REDDDDD
green=GREEEEN
blue=BLUUUUUE

echo -e "What's your most favourite colour out of the folowing \ngreen? \nred? \n blue?"

read ans
if [ red ]
     then echo "$red"
if [ green ]
     then echo "&green"
if [ blue ]
     then echo "&blue"

sleep 5

fi
```


I'm going to impliment this is a different and much more complex situation :D

---

### Post by lechien73 on 2011-12-05
Try this code instead:

```
#!/bin/bash

RED=REDDDDD
GREEN=GREEEEN
BLUE=BLUUUUUE

echo -e "What's your most favourite colour out of the folowing \ngreen? \nred? \n blue?"

read ans
if [ "$ans" = "red" ];
     then echo "$RED"
fi
if [ "$ans" = "green" ];
     then echo "$GREEN"
fi
if [ "$ans" = "blue" ];
     then echo "$BLUE"
fi
sleep 5
```

---

### Post by nothingspecial on 2011-12-05
Read this

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

Actually, read the whole guide, then look at the faq section and the pitfalls section.

---

### Post by zero2xiii on 2011-12-05
+1 for above post, read that.

The internet has a LOT of sources, but no real good "tutorials" like you will find for C, python etc.

If you plan on building complex "programs". Rather skip bash and learn python. Its very easy to learn, yet very powerful.

I would also recommend using inverted commas for the var definitions:
```
red="REDDD"
etc
```

also, learn cascading IF statements. It a very easy optimization for scripting in any language, in this script, if you enter red, it gets tested 3 times, however, doing this it will stop once the first true condition is found:

```

if [ "$ans" = "red" ]
 then
   echo "yay red"
 else
   if ["$ans" = "green" ]
     then
       echo "yay blue"
     else 
       echo "yay green" #note, this is dangerous coding practice, since ANYTHING not mathing "red" or "green" will be true here, rather place another if test here, and another else.
    fi
fi

```

Recommended:

```

if [ "$ans" = "red" ]
 then
   echo "yay red"
 else
   if [ "$ans" = "green" ]
     then
       echo "yay blue"
     else 
       if [ "$ans" = "blue" ]
         then
           echo "yay blue"
         else
           echo "Incorrect answer. Exiting"
       fi
   fi
fi

```

Please note, I am not sure all the syntax is correct. Haven't tested it. But it should give you an idea if what I meant

---

### Post by Lars Noodén on 2011-12-05
> **zero2xiii said:**
> 
also, learn cascading IF statements.

That would be [font=Courier New]elif[/font].

```

#!/bin/bash

RED=REDDDDD
GREEN=GREEEEN
BLUE=BLUUUUUE

echo -e "What's your most favourite colour out of the folowing \ngreen? \nred? \nblue?"

read ans
if [ "$ans" = "red" ];
     then echo "$RED"
elif [ "$ans" = "green" ];
     then echo "$GREEN"
elif [ "$ans" = "blue" ];
     then echo "$BLUE"
fi
sleep 5

```

---

### Post by nothingspecial on 2011-12-05
I wouldn't say skip bash. It's a great way of interacting with your linux system. :)

---

### Post by mutley89 on 2011-12-05
"&green" should be "$green". 
You also need a fi to end each if statement, they are similar to braces in other languages.

```
read ans
```This accepts input and assigns it to the variable "ans".  

```
if [ red ]
```This will always be true.  When given no options the [ test command simply tests if the arguments are non-empty.  What you want is:
```

if [ "$ans" = red ]
then
    echo "$red"
fi
```and so on

You could also use a case statement for this:
```

case "$ans" in

red) echo "$red";;
green) echo "$green";;
blue) echo "$blue";;

esac

```Have a look at "help test", "help read" and "help case" for more.  Also there is a lot here but [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) is helpful for learning more about bash scripting:

---

### Post by zero2xiii on 2011-12-05
> That would be elif.

Sure you can use elif aswell. But I am just trying to explain it on a level that will be easy to understand for Spyderkid. You can optimize that code almost to a single liner if you really wanted to get into some of the heavy stuff.

> I wouldn't say skip bash. It's a great way of interacting with your linux system. 

Agreed. I also write many complex programs inside bash and just import from scripts or programs when some function I need is not there. I am just suggesting python because spiderkid said > I'm going to impliment this is a different and much more complex situation  And I personaly have had issues with bash before if you get to complex. You dont get the result you expect, yet there is no errors, and finding what is causing the problem in bash can be a tedious task in programs over 500 lines... 

Lolz, but this is all just a personal though and opinion. Still an open choice.
Cherz

---

### Post by Spyderkid on 2011-12-05
> **zero2xiii said:**
> +1 for above post, read that.

The internet has a LOT of sources, but no real good "tutorials" like you will find for C, python etc.

If you plan on building complex "programs". Rather skip bash and learn python. Its very easy to learn, yet very powerful.

I would also recommend using inverted commas for the var definitions:
```
red="REDDD"
etc
```

also, learn cascading IF statements. It a very easy optimization for scripting in any language, in this script, if you enter red, it gets tested 3 times, however, doing this it will stop once the first true condition is found:

```

if [ "$ans" = "red" ]
 then
   echo "yay red"
 else
   if ["$ans" = "green" ]
     then
       echo "yay blue"
     else 
       echo "yay red" #note, this is dangerous coding practice, since ANYTHING not mathing "red" or "green" will be true here, rather place another if test here, and another else.
    fi
fi

```

Recommended:

```

if [ "$ans" = "red" ]
 then
   echo "yay red"
 else
   if [ "$ans" = "green" ]
     then
       echo "yay blue"
     else 
       if [ "$ans" = "blue" ]
         then
           echo "yay blue"
         else
           echo "Incorrect answer. Exiting"
       fi
   fi
fi

```

Please note, I am not sure all the syntax is correct. Haven't tested it. But it should give you an idea if what I meant

Thanks, but you've changed it so it's irrelevent to what i was going to use it for :D thanks anyway

---

### Post by Spyderkid on 2011-12-05
THANKS! lechien73

---

### Post by lechien73 on 2011-12-05
You're welcome...glad it helped :D

---

