---
title: "Help me read source code"
date: 2011-06-06
forum: General Help
---

### Post by deadfish87 on 2011-06-06
Hey,

So im a complete noob to linux trying to make the move away from programming with windows. I have just downloaded the souce code to the Fluid FLTK GUI designer version 1.3.0. and i am completely lost. It just a huge pile of folders to me i don't know where to start how do I compile it ect....? Can anyone with experience maybe give me some pointers on how the most productive way to go about reading open source metarial is? like are there any files with classic names i should be looking for in particular?

Thanks

---

### Post by r-senior on 2011-06-06
I guess the first step is to figure out what language it is. In those directories what is the predominant file extension?

Do you know what command starts the application? That should give you a clue about the starting point.

Is there a README or INSTALL file? Are there any other similar-looking files? 

Is there a file in the top-level directory called configure?

Is there anything that looks like it might be a documentation directory.

Is there a website? A Wiki perhaps?

---

### Post by Rubi1200 on 2011-06-06
This might help:
[http://en.wikipedia.org/wiki/FLTK](http://en.wikipedia.org/wiki/FLTK)
[http://www.fltk.org/documentation.php](http://www.fltk.org/documentation.php)

---

### Post by deadfish87 on 2011-06-07
hey peeps sorry for the dealyed reply.

r-senior i am new to linux and therefore have no idea what you mean by "a command to start the application"

There are several README file all of which make no sense to me...they talk about running a configure script but doesnt explain how to do this in noob language!

There is a documentation directory but there isnt really any documentation in it only Doxybook Doxyfile makefile README (yet again!) strip_tags and then loads of png files.

I have browsed through the documentation supplied by rubi, very breifly i might add but it seems to be on how to use the software not the details into how it was designed and coded.

Any further ideas that might help me?

Oh yes and most file extensions are .in or .cxx not sure what either is in linux.

Thanks

---

### Post by nothingspecial on 2011-06-07
Are you wanting to understand the source code or simply compile it to run on your machine.

The difference is between about 10 minutes to 3-6 months reading.

---

### Post by deadfish87 on 2011-06-07
could someone possibly tell me how to get it into a IDE to run it please?

maybe if i had it in an IDE it wouldnt look so alien at the moment im using KDevelop 4 not sure if it is any good though?

Thanks again

---

### Post by FormatSeize on 2011-06-07
> **deadfish87 said:**
> 
 r-senior i am new to linux and therefore have no idea what you mean by "a command to start the application"
Open a terminal, and input the following command (if you are using Ubuntu)
```

firefox
```
Firefox will then open. There are many others, some of which don't even necessarily take you to a GUI, such as cfdisk, and some that don't give you an interface, put just prints information, like hdparm.
 
> **deadfish87 said:**
> There are several README file all of which make no sense to me...they talk about running a configure script but doesnt explain how to do this in noob language!
They don't make sense because they aren't in a language that you are used to speaking, but rather a language that the computer speaks. As you look at more of them and learn more and more command, you will start to understand what the scripts are doing. You can find a beginners guide to bash scripting with little to no searching. You'll start out with a simple script like 
```

#!bin/bash
**echo **"Hello World!"
```
which will print "Hello World!" in your terminal, then move on to more complicated things. Only then will you begin to understand what these compile scripts are doing, but it can be quite some time before you understand everything about them. 
 
> **deadfish87 said:**
> There is a documentation directory but there isnt really any documentation in it only Doxybook Doxyfile makefile README (yet again!) strip_tags and then loads of png files.
 
I have browsed through the documentation supplied by rubi, very breifly i might add but it seems to be on how to use the software not the details into how it was designed and coded.
 
Any further ideas that might help me?
 
Oh yes and most file extensions are .in or .cxx not sure what either is in linux.
 
Thanks
If you are trying to install something, then don't. I would recommend waiting until you are more familiar with compiling things from source, and stick with "aptitude" or "apt-get" or the Software center.
 
Compiling from source is rather easy, though, and it doesn't even involve reading a script. I have no idea where that idea came from. It's four simple lines of code (most of the time) and it's done. If you don't see an INSTALL (it will be capitalized) in the folder from the extracted package, then you are already not on the right track. 
 
If you are wanting to compile something from source anyway, I am more than happy to help, given the name of the package. But grabbing a package and trying to understand the code and doing things outside of what an INSTALL file dictates is not something that I would recommend.

---

### Post by deadfish87 on 2011-06-07
nothingspecial, its a bit of both to be honest i wont to be able to read and understand the source code aswell as get it into some sort of IDE to run it.

coming from windows i use Visual Studio 2010 and there i can load a project like this up and view the code edit it, run it, and also see the form design/layout of the actual program too. Can you do that in linux?

Thanks

---

### Post by nothingspecial on 2011-06-07
There are tons of ides available.

Try installing codeblocks or search for others in the software center.

Also there is a programming sub-forum here

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

You will find many, many knowledgeable coders there.

---

### Post by Wim Sturkenboom on 2011-06-07
you might have some files in the root folder of what you downloaded

Is there a filecalled readme? If so, read it ;)
Is there a file called configure?
Is there a makefile?

Usual steps to install stuff from source
./configure
make
make install

You might need root privileges for the last step

google for [linux install from source](http://www.google.co.za/#hl=en&source=hp&q=linux+install+from+source&oq=linux+install+from+source&aq=0&aqi=g1g-v3g-m1g-b2&aql=&gs_sm=e&gs_upl=54l6499l0l22l20l0l4l1l1l752l5254l1.3.4.3.2.2.1&fp=e8639e9946eba69d&biw=1024&bih=403)

first hit: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by FormatSeize on 2011-06-07
> **deadfish87 said:**
> 
Coming from windows i use Visual Studio 2010 and there i can load a project like this up and view the code edit it, run it, and also see the form design/layout of the actual program too.
As a programmer, I'm sure that you will be able to pick up on it quickly, but still, there is a lot to learn if you truly want to be able to look at a script and understand what is going on. I am saying this from experience, as I program in Visual Studio at work (I do Linux at home as more of a hobby). Too, it depends on what language it's in. Most of the scripts that I look at are either [bash](http://tldp.org/LDP/abs/html/) (there's a big book for you) or [python]("http://www.osc.edu/supercomputing/training/python/python_pt1_0702.pdf") (that's a PDF).
 
> **deadfish87 said:**
>  Can you do that in linux?

 
Of course you can. I can't think of the one I was using yesterday off the top of my head, but it was in Fedora. Possibly Eclipse. But yes, there are plenty out there, and you will have lots to do. Or, something I found to be kinda cool, you can configure your text editor, Gedit, to look and feel like an IDE:
[http://www.micahcarrick.com/gedit-html-editor.html](http://www.micahcarrick.com/gedit-html-editor.html)

---

### Post by deadfish87 on 2011-06-11
Hey guys,

sorry for the delayed post...I managed to figure out how to get the software running from the source code so thanks for all the help on that.

However as this is my first time ever doing this and also first time in using libraries from an external source, i was wondering if some could just explain a couple of things for me:

1. Once the files are downloaded and have not been compiled/made yet i take it that would contain all the code used to develop the software...all the .cpp, .h, .hpp correct? so i should be able to look through them an see how the software was developed, correct?

2. how can i run the code in an IDE such as QT or Kdevelop so i can put in break points and see the code running line by line to see how it all ticks?

My apologies if this seems like "spoon feeding" not got a great deal of programming experience and non in linux.

Thanks alot for being patient ;):D

---

### Post by deadfish87 on 2011-06-11
oh yeh formatseize...thanks a bunch for the links you sent and if you could get the name of the software you were using that would be cool to.

Cheers

---

