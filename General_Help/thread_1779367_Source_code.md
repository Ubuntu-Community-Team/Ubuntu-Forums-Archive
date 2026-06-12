---
title: "Source code"
date: 2011-06-10
forum: General Help
---

### Post by jetgil on 2011-06-10
Hello all, i am new on linux.I want to programs source code on linux,but i don't know how i seen programs source code on command line.Help please :-)

---

### Post by SavageWolf on 2011-06-10
$ apt-get source program

(Where "program" is the program you want the source of). This downloads the source code, which will be placed in your current folder, so make sure to cd into a suitable place.

I'm not sure if this is what you want because you didn't explain it very well.

---

### Post by Topsiho on 2011-06-10
Hello,

First you'll have to decide what programming language you want to learn. A relatively easy language which is very powerful and modern, is Python, so you could start investigate it. It seems that Google was programmed in Python ...

Nice thing is it is already installed on your computer (I assume Ubuntu here). In a terminal you type python and there you go.

You get a prompt like >>> and next to it you type 2 + 2, then push the enter key.

This of course not programming yet, but on the web you'll find some tutorials (google python tutorial), and in Full Circle Magazine (google for it) you'll find a very extensive, and still ongoing instruction, with examples, and there is also a number of special issues for python.

Watch this: there are python 2.x and python 3.x, the latter is a newer version which is in some parts different. 2.x is used very much these days, python 3.x probably has the future.

One thing: programming in a terminal might not seem sexy, but in Python it is also possible to program GUI (graphical) programs. But first things first: try to learn Python first and then you could start programming some  eyecandy :)

Hope this helps,

Topsiho

---

### Post by jetgil on 2011-06-10
i am a computer engineer student,graduate 1 :-) so i know python.


sudo apt-get source vlc 

this command download one rar file.There are a lot of txt files in this rar file.But i have not SOURCE CODE yet :( what can i do ?

---

### Post by Topsiho on 2011-06-10
If I do this command I get a .tar.gz file, double clicking on it and unpacking gives me a list of folders and files, in which I see a src folder, which contains the sources.

Topsiho

---

### Post by oldos2er on 2011-06-10
You don't need to use 'sudo' for downloading source code. 'apt-get source vlc' will download it to your home folder, or you can get it here: [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

---

