---
title: "SH SCRIPT Syntax error: &quot;else&quot; unexpected (expecting &quot;then&quot;)"
date: 2011-03-09
forum: General Help
---

### Post by adrenalin6 on 2011-03-09
BTW, yes I did search for a solution but the only one I found said this error happened if I had an if statement on the same lines as "then".
Can you guys help me out?
Here is a part of my script,

```

if [ -f file1.jar ]; 
    then 
echo "Found: file 1.jar" 
    else  
echo "file1.jar: Missing " 
    Down  

  if [ -f file2.zip ]; 
   then 
echo "Found: file2.zip" 
   else  
echo "file2.zip: Missing " 
    Down  

  if [ -f file3.sh ]; 
   then 
echo Found: file3.sh  
   else   
echo file.sh: Missing  
    Down  

```There alot more and "Down" was defined as a function

Down() ( 
echo "my script is a type of installing script if you needed to know,"
echo "it Identifies files if there present, if not downloads them and moves them into a java game."
echo "I get a syntaz error on line 22 which is the else after found: file 1 echo"
echo "I also have #!/bin/sh at the top, I didnt copy it in"
)

Can you help me out?

---

### Post by Vaphell on 2011-03-09
use indentation because your script is unreadable and why all these empty lines?

if syntax goes like this
```
if <condition>; then
  <stuff>
else
  <stuff>
fi
```
or
```
if <condition>
then
  <stuff>
else
  <stuff>
fi

```

simply put newline and ; are synonymous in some cases.

---

### Post by vivek.pandey on 2011-03-09
you have to terminate a particular if with a corresponding fi..

---

### Post by adrenalin6 on 2011-03-09
> **Vaphell said:**
> use indentation because your script is unreadable and why all these empty lines?

if syntax goes like this
```
if <condition>; then
  <stuff>
else
  <stuff>
fi
```or
```
if <condition>
then
  <stuff>
else
  <stuff>
fi

```simply put newline and ; are synonymous in some cases.

I read somewhere to add lines because its what caused my error, sorry if it made it un readable.
No reason for double posting, I tried it on the part of my script that was having problems, sorry but same error 
"./installer.sh: 22: Syntax error: "else" unexpected (expecting "then")"

---

### Post by adrenalin6 on 2011-03-09
> **neo_aryan said:**
> you have to terminate a particular if with a corresponding fi..

Tell me if I understood

```

if < -f file1.sh >;
   then
<echo "File1">
   else
<echo "Failed">
    fi

```I read about fi but I concluded it acted like return 0; in C++ (for example)
So it's to finish an "if"?
Also Same Problem
:confused:
Error Changed after doing some editing,
its "  ./installer.sh: 24: Syntax error: "else" unexpected (expecting "}")  "

the from the start to line 24 is 

```

#!/bin/sh

pause()
{    read -n1 -t5 any_keyread -n1 -t5 any_key
    echo 
}

Start()
{
 
echo "Starting File Check"
pause
 
if [ -f crackedclient.jar ]; 

then 
    {
echo "Found: crackedclient.jar"
} 
else {
echo "crackedclient.jar: Missing " 
    Down }
fi


```
I cleaned up the useless echo lines at the top but its all the way from start to line 23.
(I will be  AFK but I will be back in 7 hours)

---

### Post by vivek.pandey on 2011-03-09
though i don know much but it is something like opening and closing braces in c++ so if you have if you should have a corresponding fi so that computer may understand which if ends here or something like that..go for a standard guide for better explanation but i think that fi is the problem for you

---

### Post by Vaphell on 2011-03-09
don't put < > there, i merely used them to indicate customizable parts of the expression :-), use real conditions in [] and normal commands. And with valid script you don't need to put an empty line between every 2 lines of code. Below example works just fine

```

#!/bin/bash

if [ -f file ]
then
  echo line1
  echo line2
else
  echo line3
fi

```

---

### Post by adrenalin6 on 2011-03-09
Thanks guys for help,
but I epicly failed, I had a pause function that didnt work but didnt know.
Now the script deleted the game files, folders and it self including all copys of itself.

Moral is: DONT KEEP BACKUPS IN SAME FOLDER WITH A SCRIPT CONTAINING rm *.
lol

-Henry

---

