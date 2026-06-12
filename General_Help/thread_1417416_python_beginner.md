---
title: "python beginner"
date: 2010-02-27
forum: General Help
---

### Post by kokoshmusun on 2010-02-27
[B]**I apologize for wrongly posting this on the installation & upgrades thread, couldn't find a way to move or delete it, so I post here again.**
[/B]             
                                                                Hi, 
I'm on Karmic/GNOME. I want to make a quick entry into the programming world and my choice is Python. It's been around 15 years since I last programmed and can be considered a total newbie (also new to Linux) so I have some questions:

1) I'm assuming I should work with Python 3.x. I have Python 2.5 and 2.6 for running programs in Ubuntu Karmic. Can I uninstall these older versions? What packages do I need for installing a programmer's version of Python 3.x?

2) I assume an IDE would be good to get familiar with. I don't have experience with any. What would you recommend for a beginner (FOSS please).

3) I've downloaded some free python documents/books online.  Any recommendations (paid books included)?

4) One of the reasons I'm getting into Python is to be able to program psychology experiments using PyEPL that I just found out. Any recommendations on how I can get started on that? I'm hoping PyEPL will save me from proprietary software and if it does, I will spread it around my academic community (I'm a soon to be asst.prof). 

I know this is a lot but anything is helpful and this forum is the one I've relied on the most for useful info as I eased into freedom (from Vista to Karmic, ahhhh...), so.... Thanks in advance.

---

### Post by oldfred on 2010-02-27
Whatever you do - DO NOT UNINSTALL PYTHON 2.6!!

Major parts of Ubuntu run on python and have not yet been upgraded to the newest version as python3 has some significant changes and many supporting files have not yet been updated. We have seen several users who have uninstalled 2.6 and it is just about a reinstall unless you are really good at chrooting into your system and reinstalling from there.

I have been playing with python as an old fortran, basic, dbase and MS Access vba  programmer. I wanted graphics so I have used glade and geany. You will get many recommendations and the advantage of linux most are free, so you can try them and see what you like. I like geany because I can just copy in sample code I have downloaded and directly run it.

I saved these sites:
Python for Informatics: Remixing an Open Book [PDF]
[https://source.sakaiproject.org/contrib//csev/trunk/pyinf/tex/book.pdf](https://source.sakaiproject.org/contrib//csev/trunk/pyinf/tex/book.pdf)

[http://diveintopython3.org/](http://diveintopython3.org/)

I have also bought a couple of books one on 2.6 and one on 3.0 but I am still using 2.6 as some of the libraries I want are still 2.6.

---

### Post by diesch on 2010-02-27
> **kokoshmusun said:**
> 

1) I'm assuming I should work with Python 3.x. 


Python 3 is incompatible with Python 2 and not all libraries are ported to Python 3 yet.
In particular it looks like PyEPL needs Python 2

> **kokoshmusun said:**
> 
I have Python 2.5 and 2.6 for running programs in Ubuntu Karmic. Can I uninstall these older versions? 

No. A lot of packages depend on python 2.6 as this is the default Python version of Ubuntu 9.10

> **kokoshmusun said:**
> 
What packages do I need for installing a programmer's version of Python 3.x?

The package *python3* contains all you need to run programs using the standard library, *python3-doc* contains the documentation and *python3-examples* some examples.

> **kokoshmusun said:**
> 
2) I assume an IDE would be good to get familiar with. I don't have experience with any. What would you recommend for a beginner (FOSS please).

I'm using just an editor (if you want to call Emacs "just an editor" ;-) ). If you want an IDE have a look at* eric*

> **kokoshmusun said:**
> 
3) I've downloaded some free python documents/books online.  Any recommendations (paid books included)?


[ A Byte of Python](http://www.byteofpython.info/) and [How to Think Like a Computer Scientist]("http://www.ibiblio.org/obp/thinkCSpy/") are good free books. In general [http://python.org/doc/](http://python.org/doc/) is a good source for python docs.

> **kokoshmusun said:**
> 
4) One of the reasons I'm getting into Python is to be able to program psychology experiments using PyEPL that I just found out. Any recommendations on how I can get started on that? I'm hoping PyEPL will save me from proprietary software and if it does, I will spread it around my academic community (I'm a soon to be asst.prof). 

I've never used PyEPL, but [http://pyepl.blogspot.com/](http://pyepl.blogspot.com/) looks interesting.

[http://www.psychopy.org/](http://www.psychopy.org/) may be interesting for you, too.

---

### Post by blur xc on 2010-02-27
I'm a python beginner, and I've chosen to make vim my python IDE.  There's a bunch of ways you can customize vim for writing python code.  

[http://www.google.com/search?q=vim+as+a+python+ide&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vim+as+a+python+ide&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

and 

[http://www.swaroopch.com/notes/Vim](http://www.swaroopch.com/notes/Vim)

BM

---

### Post by kostkon on 2010-02-27
> **kokoshmusun said:**
> 2) I assume an IDE would be good to get familiar with. I don't have experience with any. What would you recommend for a beginner (FOSS please).
Some other options for IDE
[LIST]
[*]Geany
[*]Eclipse with the PyDev plugin
[/LIST]

---

### Post by Just_SomeGuy on 2010-02-27
Python isn't my primary language but I do use it quite a bit so here's my two cents.

Most of what you'll find out there is v2.6 (or at least compatible with it) so I'd probably start there.

You'll probably get a lot of advice to use a straight up text editor, but a good IDE is priceless for productivity, refactoring, and debugging when things go wrong.
You can't beat Eclipse + the PyDev plugin. Bonus that its cross platform so you can use the same setup on any system you use.

Core Python Programming (Chun) is a great book. I've heard good things about Dive in to Python but I can't personally vouch for it.

---

### Post by kokoshmusun on 2010-02-27
Wow, thanks for the amazing answer you all (this was my first post at ubuntuforums).  It sure saved me from the horrible mistake of uninstalling the older Pythons and starting with Py3. 

I will be trying out IDEs as you suggested.

Cheers!

---

