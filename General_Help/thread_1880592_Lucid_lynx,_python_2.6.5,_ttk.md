---
title: "Lucid lynx, python 2.6.5, ttk"
date: 2011-11-14
forum: General Help
---

### Post by histamineblkr on 2011-11-14
Here's my issue:

I wrote some python scripts in vim, in Netbeans, and in gedit on my 11.04/11.10. Well I hated 11.10 and decided to just go back to 10.04 and stick with that. One of the problems I ran into is that I can not run my scripts that I original wrote nor can I even run example code/scripts that use ttk such as Style and other methods. Below is my problem:

After installing 10.04, compiling python 2.7.2 and python 3.1, and it not working I now have a fresh/pretty fresh Ubuntu 10.04 LTS Lucid Lynx installed that came with python 2.6.5. I have installed Tkinter and have Tk/Tcl 8.5 in python. The only thing I need now is ttk so I can theme my widgets and give them a little bit better appearance. 

What is the best way to get all of the ttk features onto my machine and importable?

Is there a way to compile/install ttk into python 2.6.5 on my machine? 

I have found a couple pages that seem helpful but that don't really specify how or what I need to do, such as saying:

 "If you are not sure if you have Tile installed correctly or if yourtkinter is compiled against Tk 8.5, try running the test suite:[FONT=monospace]

[/FONT]$ PYTHONPATH=ttk-gsoc/src/2.x python ttk-gsoc/src/2.x/test/runtests.py".

Link is [here]("http://svn.python.org/projects/sandbox/trunk/ttk-gsoc/README") and originates [from here]("http://svn.python.org/projects/sandbox/trunk/ttk-gsoc/"). I was just curious what would be in my $PYTHONPATH variable so I echo it but it doesn't exist or there is nothing in it. So I haven't done anything with that $PYTHONPATH variable.

Next is the python-ttk [page]("http://code.google.com/p/python-ttk/"). This page seems to be the home or some home for python ttk that offers a reference page and a current repository? Can I add this repository and then install a ttk package? I'm unsure how this page would help me out since the links aren't very helpful to me.

Next is the python 3 pyttk 0.3.2 [page]("http://pypi.python.org/pypi/pyttk/"). This page has a "pyttk-0.3.2.tar.gz" that might be useful. I haven't downloaded or installed it since I don't want to randomly add stuff that may not be helpful.

The last is a Tkinter Wiki [page]("http://tkinter.unpythonic.net/wiki/Tk85AndPython"). This page has some good info and suggests that for the best results I compile python myslef. While this sounds good in theory, I tried compiling python 2.7.2 and python 3.1 on a previous 10.04 installation but it still didn't work. I could run python2.7 or python3.1 from the command line but I would get an error running some of my previous python scripts such as "_tkinter module not found" or something close to that. I'm guessing that it had to do with the module not being compiled correctly when I did the "./configure" and "make".

Hopefully some kind person can now tell me how to get ttk onto my 10.04. I would be happy with anyway really; whether it be getting ttk into python 2.6.5 or installing python 2.7.2 or installing python 3.1. I just want a way that works. 

Thank you for all your help.

---

### Post by ltpriest on 2011-11-14
I am having similar problems.  Although I have gotten ttk to work under Ubuntu10.4 python3.1, I am still confused as to why it will not work in the python 2.6?  as a beginner I would suggest switching to the python 3.x to get ttk working...
good luck

P.S. the 2to3 thingy worked to convert all of my working projects to Python 3.1 and that has helped a lot.

---

### Post by histamineblkr on 2011-11-15
Did you have a good way to switch to 3.1? I tried getting the package and installing 3.1 but it still didn't work so I'm guessing I did something wrong...

---

### Post by histamineblkr on 2011-11-17
> **histamineblkr said:**
> Here's my issue:

I wrote some python scripts in vim, in Netbeans, and in gedit on my 11.04/11.10. Well I hated 11.10 and decided to just go back to 10.04 and stick with that. One of the problems I ran into is that I can not run my scripts that I original wrote nor can I even run example code/scripts that use ttk such as Style and other methods. Below is my problem:

After installing 10.04, compiling python 2.7.2 and python 3.1, and it not working I now have a fresh/pretty fresh Ubuntu 10.04 LTS Lucid Lynx installed that came with python 2.6.5. I have installed Tkinter and have Tk/Tcl 8.5 in python. The only thing I need now is ttk so I can theme my widgets and give them a little bit better appearance. 

What is the best way to get all of the ttk features onto my machine and importable?

Is there a way to compile/install ttk into python 2.6.5 on my machine? 

I have found a couple pages that seem helpful but that don't really specify how or what I need to do, such as saying:

 "If you are not sure if you have Tile installed correctly or if yourtkinter is compiled against Tk 8.5, try running the test suite:[FONT=monospace]

[/FONT]$ PYTHONPATH=ttk-gsoc/src/2.x python ttk-gsoc/src/2.x/test/runtests.py".

Link is [here]("http://svn.python.org/projects/sandbox/trunk/ttk-gsoc/README") and originates [from here]("http://svn.python.org/projects/sandbox/trunk/ttk-gsoc/"). I was just curious what would be in my $PYTHONPATH variable so I echo it but it doesn't exist or there is nothing in it. So I haven't done anything with that $PYTHONPATH variable.

Next is the python-ttk [page]("http://code.google.com/p/python-ttk/"). This page seems to be the home or some home for python ttk that offers a reference page and a current repository? Can I add this repository and then install a ttk package? I'm unsure how this page would help me out since the links aren't very helpful to me.

Next is the python 3 pyttk 0.3.2 [page]("http://pypi.python.org/pypi/pyttk/"). This page has a "pyttk-0.3.2.tar.gz" that might be useful. I haven't downloaded or installed it since I don't want to randomly add stuff that may not be helpful.

The last is a Tkinter Wiki [page]("http://tkinter.unpythonic.net/wiki/Tk85AndPython"). This page has some good info and suggests that for the best results I compile python myslef. While this sounds good in theory, I tried compiling python 2.7.2 and python 3.1 on a previous 10.04 installation but it still didn't work. I could run python2.7 or python3.1 from the command line but I would get an error running some of my previous python scripts such as "_tkinter module not found" or something close to that. I'm guessing that it had to do with the module not being compiled correctly when I did the "./configure" and "make".

Hopefully some kind person can now tell me how to get ttk onto my 10.04. I would be happy with anyway really; whether it be getting ttk into python 2.6.5 or installing python 2.7.2 or installing python 3.1. I just want a way that works. 

Thank you for all your help.

So if anyone wants to know; it turns out that just installing the "pyttk-0.3.2.tar.gz" from [here]("http://pypi.python.org/pypi/pyttk/") will solve the issue of python 2.6.5 not having ttk. Download the .tar.gz, unpack it, cd into the folder, and run "python setup.py install" and you'll be golden.

---

