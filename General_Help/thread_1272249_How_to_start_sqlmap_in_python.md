---
title: "How to start sqlmap in python"
date: 2009-09-21
forum: General Help
---

### Post by TR14RC3 on 2009-09-21
Hello,
 I was wondering if anyone knows how to start sqlmap in python? I have searched and searched for information about it, but most of the info is not what I am looking for. I am just wondering what is the command to get it going. Or if you know a good tutorial you could point me at. I have tried sveral commands from other post with no luck. I am running ubuntu 9.04. Any help would be appreciated. Thanks.

---

### Post by Mighty_Joe on 2009-09-22
did you try reading the [documentation]("http://sqlmap.sourceforge.net/doc/README.html")? It has several examples.

---

### Post by TR14RC3 on 2009-09-22
Yes I did and it does not really say start sqlmap by entering (the command) thats all I want to know. The instructions are not that great. Just like most. I have been messing with it for days. The instructions don't do justice. I just keep getting error messages. It is a simple question. What is the command to start sqlmap? From there I think I can get it. There are no clear instructions out there. I can understand why, but I need a little help here. I always do my homework and have contributed any info that I have in my blog and on here. I try to explain things the best and simplest way for people to understand, but most directions I come across do not explain very well. I just want to know how to start the program, I am not an expert in python so I figured  I would see if anyone could give a straight answer. The documentation has examples, but they don't really make sense unless you know how to start sqlmap or may not even if you know how to start it. But starting the program is a good way to begin.


Really, at this point I am just trying to see if I have it installed correctly. I can't tell though because I don't know the exact command. I have tried some, but get error messages. So either it is not installed right or I am using wrong command. I am trying to figure out which one.

---

### Post by Mighty_Joe on 2009-09-22
> **TR14RC3 said:**
> Yes I did and it does not really say start sqlmap by entering (the command) thats all I want to know. 

Have you tried:
```
sqlmap
```
?

I've never touched the thing and it seems all one does is invoke:
```
sqlmap -u http://someurl
```
and it tests various sql injection attacks.

---

### Post by TR14RC3 on 2009-09-22
This is what I get:

tr14rc3@tr14rc3-1337:~$ python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> sqlmap
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'sqlmap' is not defined

and the same thing with the other that you suggested.

Maybe it needs a path to the file like sqlmap/usr/local/bin.....?

---

### Post by Mighty_Joe on 2009-09-22
Don't start Python first.  Just open a console (xterm, whatever) and type in "sqlmap".
However, if you want to run sqlmap from within Python because you are creating a test script or something like that, you should look at the [subprocess]("http://docs.python.org/library/subprocess.html") module

---

### Post by TR14RC3 on 2009-09-22
Derp! They made it sound like you need to run it in python. Thats what I did not get. Thanks. I feel dumb now.

---

