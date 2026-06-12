---
title: "Start learning python ?"
date: 2012-02-06
forum: General Help
---

### Post by cotcot on 2012-02-06
I have a spreadsheet doing a lot of calculations based on figures put in by the user with a couple of graphics showing diagram and sketches. I am struggling with compatibility problems between libreoffice and excel and even with excel versions (excel 2007 makes a mess from what i have setup in excel 2003 !).
So I am wondering if it is worth learning programming to convert the excel application in for instance a python application. I read about it and so i came across Tkinter as a gui designer for python.

My question is if it is worth to learn python and if so what might be a wild guess for the learning time (assuming I have 10 hours a week time for it) ? I have some programming experience from loooong time ago (198x) with Basic and Fortran.

---

### Post by lykwydchykyn on 2012-02-06
That's tough to gauge.  Python is a pretty simple language, and apart from a few unique aspects (like using whitespace to delimit blocks) it pretty much does what you expect a language to do.  Probably you can learn the core syntax in a couple hours.  Where most people struggle at first is learning to write idiomatically and take advantage of built-in features (e.g., using list comprehensions or iterators instead of for/while loops).

Tkinter is a GUI API, I'm not aware of it having any sort of graphical designer program.  IMHO it's simple to learn, though somewhat limiting with a few surprising omissions.  It does have a fairly powerful canvas widget, which may be useful to you in this instance with the charts and graphs.

How are you with object-oriented programming?  Pretty much any GUI programming is going to involve OOP.

---

### Post by cotcot on 2012-02-06
> **lykwydchykyn said:**
> 
How are you with object-oriented programming?  Pretty much any GUI programming is going to involve OOP.

Oop is fully new to me. My programming experience is from before 1990 (except from some visual basic). 
I am not sure where to begin. I started a tutorial of python where I recognize the principles from earlier times; indeed easy. But then comes the window stuff to make for instance a table for data to be supplied by the user or windows showing a graphical result of calculations. There I do not see yet where to start. 
This oop looks to me as a lot of instructions to learn. Also how to discover which class for instance to use for what goal. Looks like if your not busy with this all day you start forgetting a lot.

---

### Post by MG&amp;TL on 2012-02-06
I suspect you'll find you're bitten with the programming bug and you will be busy all day. ;)

You could always try Gtk-which does have a GUI designer called glade-not sure how to use it though. If I'm honest, it also looks a lot better the TKinter.

---

### Post by lykwydchykyn on 2012-02-06
It's difficult at first, but once you get the basic idea of OOP figured out it makes more sense.

There's a good tutorial here:

[www.pythonware.com/library/tkinter/introduction/](www.pythonware.com/library/tkinter/introduction/)

I suggest for a day or two to forget about your application and just focus on learning the language, API, and methodology abstractly.  Before long the approach will start to become clear.

---

### Post by JCoop on 2012-02-07
Your situation sounds a lot like mine. I originally got interested in Python because I wanted to design an application for a website I was working at, but I had no programming experience. After some reading, I decided that Python would be the easiest language to start with and it was one of the best decisions I ever made. 

The best way to approach it is to just dive right in. You are not going to learn without actually seeing how the language works using something like IDLE, where you can get immediate feedback. Once I understood the basic operations, I moved on to trying to build something I was used to dealing with, a GUI. Tkinter is very popular and included in the standard Python library, but the easiest GUI language in my opinion is wxpython. It is just wxwidgets ported from the C language.It has a lot of available documentation and it would be difficult to make it any more user friendly.

You will have to download wxpython and just like Python itself, you will have to learn some new coding conventions. From the time I read my first Python book to the time I started building the GUI was probably three weeks. I found the best way to do this was to use a Rapid Application Developer (RAID) called wxGlade. It is like a visual building block set for your app. While you are playing with the visual design (and learning the quirks of using sizers in wxGlade), you can also be continuing to read about how to use Python. 

Once the GUI is built, you can start to go back in and "hook everything up." This is where I learned the most about coding. You will have to manipulate the elements of both Python and wxPython which can at times be extremely frustrating. Luckily, Python is so forgiving that you can assemble working code from a crude, taped together, unorganized, mess... and it will work! Later, once you start to get more time and knowledge under your belt, you can revisit your original code and clean it up to be more efficient and professional looking. The two biggest pieces of advice I can offer are 1) Dont be afraid to get up and walk away (It's not quitting and your best ideas will happen when you return every time) and dont avoid something because it seems like it may be too complicated. Ask questions, but the greatest gains will come from the solutions you find through experimentation. Try and alternate between a book on Object Oriented Programming and one on Python (a few pages from each everyday). I could have avoided a lot of confusion by doing that.

Sorry for the long post, but learning Python was a real "aha!" moment for me and opened the doors into a lot of other programming adventures. I always encourage others to try it out. Good luck!

---

### Post by cotcot on 2012-02-07
A great thanks for all replies. Very useful ! For the python part I am half way in 'A byte of python'. For the GUI I am looking for books/tutorials. There are lot of them. The problem is more which ones to read. I think I will start with the tkinter tut from the link of lykwydchykyn and search for a tut of wxglade. Seems a good idea to study python and tkinter (or alternative) in parallel.
Does it make sense to use Glade instead of wxglade, tkinter or so. Glade seems to be a GUI to make a window without having to know the commands. (just like drawing tool saving to xml). Or is wxglade/tkinter better once you are familiar the classes and so on ?

---

### Post by MG&amp;TL on 2012-02-07
> **cotcot said:**
> A great thanks for all replies. Very useful ! For the python part I am half way in 'A byte of python'. For the GUI I am looking for books/tutorials. There are lot of them. The problem is more which ones to read. I think I will start with the tkinter tut from the link of lykwydchykyn and search for a tut of wxglade. Seems a good idea to study python and tkinter (or alternative) in parallel.
Does it make sense to use Glade instead of wxglade, tkinter or so. Glade seems to be a GUI to make a window without having to know the commands. (just like drawing tool saving to xml). Or is wxglade/tkinter better once you are familiar the classes and so on ?

The way glade works is that Gtk (the GUI toolkit) reads the xml file you generate, then you have to 'link up' the code you've written to the interface. Alternatively, once you understand OOP, making your own interface is really not that difficult.

---

### Post by lykwydchykyn on 2012-02-07
The tools really depend on what toolkit you want to use, and that becomes a personal decision.  I went through just about all of them before deciding that QT was the best for my needs and work habits.

Tkinter is a good place to start, and since it ships as part of Python on many OS's, it's good to know no matter what you end up using.  I wouldn't want to develop a major application with it, but it's not all bad.

There's really no one toolkit that outshines the rest, though.  If Tkinter doesn't click with you, try something else.

---

### Post by afz12 on 2012-02-07
Interesting post cotcot. I also intend to learn Python this year and have a number of tutorials I've been reading. I don't have a programming background but Python does seem to be structured intuitively. Good luck.

---

### Post by ratcheer on 2012-02-07
This is just a suggestion. I recommend that in order to gain a full grasp of OOP, learn Smalltalk first. It is OOP from the ground up. A very high percentage of Smalltalk is written in Smalltalk, so you can learn a lot about it just by examining it.

It is a fairly strange environment, but take a look at [http://squeak.org/](http://squeak.org/)

If you do try this, once you learn Smalltalk, other OOPL's are like falling off a log.

Tim

---

### Post by cotcot on 2012-02-08
Thanks a lot for all advices. 
It is more clear for me now. I know better what to do now and will eventually come back with more specific questions in new threads. Therefore I will mark this one as SOLVED.

---

