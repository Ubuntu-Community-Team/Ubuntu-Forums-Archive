---
title: "Get python to access saved programs from IDLE"
date: 2010-04-12
forum: General Help
---

### Post by oleink on 2010-04-12
Hey,
I am trying to use python and save a file in IDLE.  I finally (after changing some accesses) got to save my file BUT I don't know how to get python to access the folder I saved in.  I know python is supposed to be capable loading saved IDLE files and running the saved program.  How can I get python to access my IDLE file?

---

### Post by oleink on 2010-04-12
PS I am getting this:

Type "help", "copyright", "credits" or "license" for more information.
>>> !/home/helloworld.py
  File "<stdin>", line 1
    !/home/helloworld.py
    ^
SyntaxError: invalid syntax
>>> #!/home/helloworld.py
... 
>>> home/helloworld.py
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'home' is not defined
>>> #!/home/helloworld.py
...

---

### Post by wojox on 2010-04-12
Paste your helloworld.py script up here.

---

### Post by oleink on 2010-04-12
Here it is

---

### Post by wojox on 2010-04-12
```

#!/usr/bin/python
# Filename : helloworld.py
print 'Hello World'

```

Then open your terminal ( not idle ) and run:

```
python helloworld.py
```

If you are using IDLE, use the menu Edit -> Run Script or the keyboard shortcut Ctrl-F5.

---

### Post by oleink on 2010-04-12
Ok what do you mean? am I supposed to put it in a folder named "python"??  I haven't saved to usr/bin.  I have it saved to my home folder because I don't have any folder in bin named python so I couldn't save it there... I havent created a folder named python either

---

### Post by oleink on 2010-04-12
wrong post

---

### Post by wojox on 2010-04-12
Open gedit and copy and paste that in a file and save it in your home folder as helloworld.py

Then open your terminal and run:

```
python helloworld.py
```

You PM 'ed me a question and I told you how to set up a bin folder in your user folder and set the PATH in .bashrc. How did that work out?

---

