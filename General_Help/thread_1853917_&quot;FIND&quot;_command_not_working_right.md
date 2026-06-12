---
title: "&quot;FIND&quot; command not working right"
date: 2011-10-03
forum: General Help
---

### Post by 100m on 2011-10-03
I discovered a problem using the find command. 
 
I had a friend who uses a different distribution try it and it works for him. However, on Ubuntu (bash shell) the command doesn't work. 
 
find / -maxdepth 3 -name *.txt -ok /bin/more {} \; 2>/dev/null
 
The issues is that if I removed "2>/dev/null" then it works. 
OR if I remove "-ok /bin/more {} \;" then it works. 
It is like those two arguments don't like to work together. 
 
However, as I stated the whole command works on Cygwin - but NOT ubuntu. 
 
Is there a different forum I should be posting this problem in?
 
Or does anyone know what the problem is?

---

### Post by sisco311 on 2011-10-03
Hi and welcome to the forums!

There is no problem. :)

You don't see the prompt because -ok writes it to standard error and you redirect STDERR to /dev/null
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/find.html#tag_20_47_11](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/find.html#tag_20_47_11)

---

### Post by ofnuts on 2011-10-03
> **100m said:**
> I discovered a problem using the find command. 
 
I had a friend who uses a different distribution try it and it works for him. However, on Ubuntu (bash shell) the command doesn't work. 
 
find / -maxdepth 3 -name *.txt -ok /bin/more {} \; 2>/dev/null
 
The issues is that if I removed "2>/dev/null" then it works. 
OR if I remove "-ok /bin/more {} \;" then it works. 
It is like those two arguments don't like to work together. 
 
However, as I stated the whole command works on Cygwin - but NOT ubuntu. 
 
Is there a different forum I should be posting this problem in?
 
Or does anyone know what the problem is?

Nothing to addd to sisco311's answer explaining why your command won't work. 

However you have better put quotes around "*.txt" because otherwise "*.txt " will be filename-expanded if you have .txt files n your currrent directory when you execute the command in this form. If you have several you'll just get an error message because this will expand to "-name foo1.txt foo2.txt foo3.txt" which isn't a valid syntax, but if you have only one foo.txt then your command expands to "-name foo.txt" and it will run without trying to match other .txt files and you won't notice the problem.

---

### Post by 100m on 2011-10-03
Thanks for that fast answer.

Is there a way to do this then? I mean the issue is that you get error messages because you don't have rights to all directories.
Typically I've seen the supression done by redirection those errors. Is there another way to supress those errors but still be able to run an executible command?

---

