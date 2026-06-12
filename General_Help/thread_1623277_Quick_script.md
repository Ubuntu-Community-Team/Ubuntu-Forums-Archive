---
title: "Quick script"
date: 2010-11-16
forum: General Help
---

### Post by ghostzen on 2010-11-16
Hello all,
I am sorry if I am in the wrong section of the forum.  Could someone please help me with my script.  

```
#!/bin/sh
set -e
echo "Please enter..."

read prefix;
if [ $prefix = q ]
then
echo "Goodbye!"
elif [ $prefix = nh -o re -o st -o hp -o n2 -o po -o nk ]    
then
echo "xyz"
else
echo "Unknown?"
fi
```

I cannot get it to give me the "Unknown?" output.  How do I fix my script so that it will give me "Unknown?" when I type in an incorrect prefix?  

Thanks so much

---

### Post by papibe on 2010-11-16
Without knowing exactly what the script is supposed to do, this is going to a be a wild guess:
```
#!/bin/sh
set -e

echo "Please enter..."
read prefix

case $prefix in
 "q" )	echo "Goodbye!"
	;;
 "nh" | "re" | "st" | "hp" | "n2" | "po" | "nk" )
	echo "Doing something else."
	;;
  * )	echo "Unknown?"
	;;
esac

``` 
I hope it helps.

---

### Post by ghostzen on 2010-11-16
Hi papibe,
thank you for the quick reply, and thank you for the correction.  It is ALIVE!!! Muahahaha.  j/k :).  Thanks again.

---

### Post by ghostzen on 2010-11-16
Hi papibe and everyone.  I also have a question.  Where I wrote: elif [ $prefix = nh -o re -o st -o hp -o n2 -o nk ], I understood the syntax of this line was wrong.  I have figured by pure luck and it goes like this: elif [ $prefix = nh -o $prefix = re ....].  But I am thinking there has to be a better way to script this line elif [ $prefix = ....... ] using if, then, else statement.  thanks :).

---

### Post by papibe on 2010-11-16
This maybe help you, but I still don't know what you want to accomplish with your script. If you give us more info, maybe you'll get a better suggestions.

Nevertheless, using just if/then/else:
```
#!/bin/sh
set -e

echo "Please enter..."
read prefix

if [ $prefix = "q" ]
then
	echo "Goodbye!"

elif	[ $prefix = "nh" ] ||
	[ $prefix = "re" ] ||
	[ $prefix = "st" ] ||
	[ $prefix = "hp" ] ||
	[ $prefix = "n2" ] ||
	[ $prefix = "po" ] ||
	[ $prefix = "nk" ]
then
	echo "Doing something else."
else
	echo "Unknown?"
fi

```

You can also use these kind of shell shortcuts:
```
#!/bin/sh
set -e

echo "Please enter..."
read prefix

[ $prefix = "q" ] && echo "Goodbye!" && exit

[ $prefix = "nh" ] ||
[ $prefix = "re" ] ||
[ $prefix = "st" ] ||
[ $prefix = "hp" ] ||
[ $prefix = "n2" ] ||
[ $prefix = "po" ] ||
[ $prefix = "nk" ] && echo "Doing something else." && exit

echo "Unknown?"

```

Regards.

---

### Post by ghostzen on 2010-11-16
Hi papibe,
thanks again.  Basically, I am writing this script so that when I type in the prefix, it will run a command that is associated to the prefix.  Else, it will give me an "unknown".  For example, when I enter re it will run sudo /config/etc/...$prefix (which is re).  
Please see below.  Originally, I had this:

#!/bin/sh
set -e

echo "Please enter the prefix of the project directory:
     (Prefix: hp, n2, nk, nh, po, re, st, or q to quit)"

read prefix;

if [ $prefix = q ]
then
echo "Goodbye!"

elif [ $prefix = nh -o re -o st -o hp -o n2 -o po -o nk ]
then

   case $prefix in
        hp) sudo vi /local/etc/hp ;exit;;
        re) sudo vi /local/etc/../re ;exit;;
        .... 
    esac



else
echo "Unknown?"
fi

---

### Post by papibe on 2010-11-16
You can use the variable itself while calling an external program. For example:
```
#!/bin/sh
set -e

echo "Please enter..."
read prefix

case $prefix in
 "q" )	echo "Goodbye!"
	;;
 "nh" | "re" | "st" | "hp" | "n2" | "po" | "nk" )
	/local/etc/$prefix
	;;
  * )	echo "Unknown?"
	;;
esac

```

---

### Post by ghostzen on 2010-11-16
papibe,
your scripts are very helpful.  I've tested your scripts, and they worked. I appreciate you taking the time to help me.  :)

---

