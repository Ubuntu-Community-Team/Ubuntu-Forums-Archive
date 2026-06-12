---
title: "problem with writing expression with variable with sed"
date: 2011-08-31
forum: General Help
---

### Post by soumiksarkar on 2011-08-31
Hello all,

while i was writing the following sed expression using variable NEW_PATH it didn't work

NEW_PATH=/home/user/Pictures/new.jpg

echo there \( | sed -e 's/^there (/there ("'$NEW_PATH'", /'

where NEW_PATH is the path to a file.
I tried other variants like:

echo there \( | sed -e 's/^there (/there ("$NEW_PATH", /'

but it resulted in writing $NEW_PATH instead of the value within

I tried replacing ' ' with " " still didn't work. 

Also I have replaced / in NEW_PATH with \/ , but it isn't working

Please help

Thanks in advance :)

---

### Post by iponeverything on 2011-08-31
try not quoting the variable, and when posting don't truncate your expressions - some us of don't want to expend any more effort than necessary in helping folks.

---

### Post by papibe on 2011-08-31
Try diving the expression in two. First create the sed expression and then call sed. Something like this:
```
sedex="s/^there \(/there \("$NEW_PATH", /"
echo there | sed -e "$sedex"
```
I that works for you?
Regards.

P.D.: please use code tags (#).

---

### Post by soumiksarkar on 2011-08-31
@iponeverything : thank you for the suggestion ... will keep it in mind

actually i needed the quotes
the desired expression is:

there ("/home/user/Pictures/new.jpg",      
## a space after the comma

@papibe : your suggestion gave this error:

sed: -e expression #1, char 23: unknown option to `s'

---

### Post by soumiksarkar on 2011-08-31
Actually the problem is not the space after there, error comes in the variable part:
Sometimes I get this output:
there ("$NEW_PATH",
and sometimes an error.

---

### Post by papibe on 2011-08-31
> **soumiksarkar said:**
> there ("/home/user/Pictures/new.jpg", 
If that the output you need?

Since you are not really changing any on NEW_PATH (just adding something at the beginning and the end), sed is really not necessary. How about this:
```
#!/bin/bash
NEW_PATH=/home/user/Pictures/new.jpg
new="there(\""$NEW_PATH"\", "
echo $new

```
Is that help?
Regards.

---

### Post by soumiksarkar on 2011-08-31
actually I need sed so that I can change equivalent problem in a script.
The above problem is just an indicator of the problem.

I have tried to modified the script in this way:

exp1=`gawk -F", " '{ sum=$1", "$2 }; END { print sum }' test`
exp2=`gawk -v nu=$NEW_PATH -F", " '{ sum=$1", \""nu"\", "$2 }; END { print sum }' test`
sed -ie 's/'$exp1'/'$exp2'/' ~/test

but again '$exp1' creates problems

---

### Post by bodhi.zazen on 2011-08-31
Your problem is you are single quoting a variable.

Try this script

> #!/bin/bash
exp1="it works"
echo "$exp1"
echo '$exp1'

chomd a+x script

```
bodhi@Fedora: ./script

it works
$exp1
```

Now try this script

```
#!/bin/bash

exp1='broken'
exp2='works'

echo "it broken" | sed s"/$exp1/$exp2/"
```

---

### Post by soumiksarkar on 2011-08-31
Thank you this helped a lot :)
That was true
But still the expression i had written (which is the output of a command) can't be incorporated inside ' ' . It gives the following error:
}: command not found
END: command not found

The file ~/test is :

#!/usr/bin/perl
my @Image = ("/home/user/Pictures/k1.png", "/home/user/Pictures/k2.jpg", "/home/user/Pictures/k3.jpg", "/home/user/Pictures/k4.jpg");

and i want to insert a new path (present in $NEW_PATH) in the array.

---

### Post by soumiksarkar on 2011-09-02
Thanks to all, I solved the problem :

EDITED_PATH=$(echo "$NEW_PATH" | sed -e 's/\//\\\//g' | sed -e 's/\ /\\\ /g' | sed -e 's/(/\\\(/g'  | sed -e 's/)/\\\)/g' )
sed -ie '2s/);$/, \"'$EDITED_PATH'\");/' ~/test

Cheers :)

---

