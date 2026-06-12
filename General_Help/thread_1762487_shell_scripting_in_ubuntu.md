---
title: "shell scripting in ubuntu"
date: 2011-05-19
forum: General Help
---

### Post by saj1919 on 2011-05-19
I am using Ubuntu 11.04 and have started learning shell scripting.
Following commands do not work in shell...though have given in books and online tutorial also.

array_var=(1 2 3 4 5 6) #declaration
array_var[0]="test1"    #declaration
$ echo ${array_var[0]}  #printing single element of array

But extensive search gives me 

my_array="a b a a c"
        This is working. But now i want to print particular element of it. 
exm. $echo my_array[0] 
       should print a

**code :**

#!/bin/bash
my_array="a b a a c"
echo $area[0]
echo ${area[0]}

**error:**

trial1.sh: 4: Bad substitution

Any help !!!!! 
But as I said please do it for Ubuntu 11.04.
Is it a Bug ????

---

### Post by ysangkok on 2011-05-19
This is not a bug. The commands you are trying to execute are not Bourne shell or Bash shell commands. It looks like PHP or Perl. What is your book called?

You can use PHP and Perl under Linux. You can use the Software Center to install them.

EDIT: Also, how come you declare the "array" (it's actually not an array if you use quotes to declare it, it's a string) as "my_array". Then you refer to "area". How can you expect it to work when the variable names aren't even equal?

---

### Post by TeoBigusGeekus on 2011-05-19
```
#!/bin/bash
my_array=(a b a a c)
echo ${my_array[0]}
```

---

### Post by mcduck on 2011-05-19
> **saj1919 said:**
> 
my_array="a b a a c"
        This is working. But now i want to print particular element of it. 
exm. $echo my_array[0] 
       should print a

You aren't declaring an array here, just a single string variable. to declare an array with values a, b, a, a and c you'd do this instead:
```
my_array=(a b a a c)
```
the echo command fails simply because you are trying to read from an array while the my_array is actually just a single variable.

> **saj1919 said:**
> 
**code :**

#!/bin/bash
my_array="a b a a c"
echo $area[0]
echo ${area[0]}

**error:**

trial1.sh: 4: Bad substitution


..and once again, you are declaring a single string variable, not an array. Also check the name of the variable you are trying to read from... ;)

edit. too slow. That's what you get from trying to format your posts nicely. :D

---

### Post by Plueonic on 2011-05-19
Others have already pointed out whats wrong with the script, so;
> **saj1919 said:**
> 
trial1.sh: 4: Bad substitution

Sounds like its being executed in dash. Simply use the name of the script to run it (you already have a shebang to use bash), not *sh *trial1.sh - which points to dash

---

