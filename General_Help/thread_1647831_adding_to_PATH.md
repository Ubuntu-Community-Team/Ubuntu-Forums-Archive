---
title: "adding to PATH"
date: 2010-12-17
forum: General Help
---

### Post by 3rr0r on 2010-12-17
I am running Ubuntu 10.04 which has python 2.6.5.  A python script I use requires python 2.6.2 and I have compiled that in a seperate folder.  I want to invoke my python scripts from path without always having to physically copy my script to the directory I am in or type the full path of my script everytime I want to run it.  All this is so I can analyze pdf files.

I'm not sure if this requires aliases/path modifications/symbolic links/etc... Please help me.

**CURRENTLY**
[LIST]
[*]requires full path to python 2.6.2 interpreter
[*]requires a copy of the python script in the local directory (or type full path of where its stored)
[/LIST]
This is what **I HAVE**```

user@ubuntu:~/Desktop/py$ pwd
/home/user/Desktop/py
user@ubuntu:~/Desktop/py$ ls
file.pdf  pdf-parser.py
user@ubuntu:~/Desktop/py$ /usr/local/src/Python-2.6.2/python pdf-parser.py file.pdf
```


**DESIRED**
[LIST]
[*]python 2.6.2 is invoked with an alias
[*]pdf-parser.py is invoked with an alias/symbolic link (?)
[/LIST]
This is what **I WANT**
```
user@ubuntu:~/Desktop/py$ pwd
/home/user/Desktop/py
user@ubuntu:~/Desktop/py$ ls
file.pdf
user@ubuntu:~/Desktop/py$ python262 pdf-parser file.pdf
```

---

### Post by papibe on 2010-12-17
Instead of an alias you could use the #! on the beginning of the script to tell explicitly which program is going to interpret your script. For example, this python script would run on the default's system version:
```
#!/usr/bin/python
print "Hello, World."

```
but this one is going to be run under your 2.6.2 installation:
```
#!/usr/local/src/Python-2.6.2/python
print "Hello, World."

```
If you add the execute bit to your files:
```
$ chmod a+x myscript.py
```
You can run both from the command line like this:
```
$ ./myscript.py
```
I hope it helps.

---

### Post by JKyleOKC on 2010-12-17
You could put this line into your (hidden) ~/.bashrc file, right after the existing "alias" definitions:

```
alias py262="/usr/local/src/Python-2.6.2/python"
```

I abbreviated the alias to just py262 for no reason other than saving keystrokes when you use it (the same reason that we have ls instead of list, and "cd" instead of "change_directory"). Actually you can name it anything you want to so long as it doesn't conflict with existing aliases or commands.

---

### Post by 3rr0r on 2010-12-17
@papibe So if I edit the python script such that it directly calls the correct version interpreter, and then alias the script I should be able to call the script and correct interpreter without having either in the same directory I will be working in?

> **JKyleOKC said:**
> You could put this line into your (hidden) ~/.bashrc file, right after the existing "alias" definitions:

```
alias py262="/usr/local/src/Python-2.6.2/python"
```

I abbreviated the alias to just py262 for no reason other than saving keystrokes when you use it (the same reason that we have ls instead of list, and "cd" instead of "change_directory"). Actually you can name it anything you want to so long as it doesn't conflict with existing aliases or commands.

I did this.  I alias'd the python interpreter and the python script and it seemed to have trouble when two aliases were being called on the same line.




EDIT:  Okay!  I edited the python.py script so that it directly invoked the 2.6.2 interpreter in the source code.  Then chmod'd each .py script that I plan on using.  Then I created an alias in .bash_aliases for each python.py script so I can call it anywhere without having to have a copy of the .py file or provide the full path every time.  AND IT WORKS PERFECTLY NOW !!!  Thank you so so much :)

---

### Post by JKyleOKC on 2010-12-18
> **3rr0r said:**
> I alias'd the python interpreter and the python script and it seemed to have trouble when two aliases were being called on the same line.Just for future reference, the "alias" action only works for commands -- the first word on the line. It's never called for the arguments (the remaining words on the line).

Good to hear that you have things working now; the "#!" line at the top of each script is an extremely powerful tool...

---

