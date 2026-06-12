---
title: "Newbie - Becoming a power user - from clueless to master ?"
date: 2011-09-29
forum: General Help
---

### Post by rishi_singh on 2011-09-29
Ok, apologies first for all the hateful comments about linux. I am a complete newbie to linux and i am not very familiar with internals of computers. I see people giving me commands that i dont understand. But they do the job.

I want to understand each command, i want to be able to troubleshoot and get things working. I dont want to be confused. 
**How to become a linux pro ? What are the books,tutorials etc that will be good for this **(to remind you, i am a newbie) ?** I want to understand linux in and out. I heard that linux originated from unix. So, is learning linux like learning unix ?**

---

### Post by Idefix82 on 2011-09-29
I wouldn't recommend burying yourself in books. Just ask and google when you want to do something specific, and when you do find out how to do it, understand every bit of the command. You can also ask here "how does the command work that you just gave me". Most people will be very happy to answer.

You can safely assume that almost any administrative task you want to do can be done with the command line, so whenever you do something with the graphical interface, you can just ask yourself "how would I do it in the terminal". In many cases, once you know how to do it, the CLI will be by far the more efficient way of doing things. Here are some examples: crop or resize a picture (or 900 pictures in one go), send an email, move, copy, rename files, backup an entire folder in a neat .tar archive, find all files that were changed within the last 3 hours and whose name starts with "foo" but does not contain a space, delete the commas at the end of each line in a text file,...

Your best friend will be the man command. E.g. if you remember that the command tar was used for archiving, but do not remember all the options, type in
```

man tar

```
in the terminal to remind yourself of the syntax.

Once you get past the basic tasks, such as moving files, changing permissions and so on, learn sed and awk (tutorials on the internet abound). Above all, enjoy exploring your computer and don't bury yourself in books.

---

### Post by dave01945 on 2011-09-29
a good one to start with would be 

```
man apropos
```

apropos searches the man page using keywords so if you don't know what command you need you can use apropos to try and find a command

---

### Post by rishi_singh on 2011-09-29
> **dave01945 said:**
> a good one to start with would be 

```
man apropos
```apropos searches the man page using keywords so if you don't know what command you need you can use apropos to try and find a command

Aha !

---

### Post by bodhi.zazen on 2011-09-29
Learn to use the command line:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

Learn to use regular expressions, sed, grep, awk

Learn to read the man pages

---

### Post by fixerdave on 2011-09-30
> **rishi_singh said:**
> ... I see people giving me commands that i dont understand. But they do the job.
...

And, that is the power of Linux.  Ask for help on a forum for a Windows system and you wind up with either an endless series of screen-captures or great gobs of "click here, then the File tab, the check the properties..."  It's so annoying to try to give anyone instructions on doing anything like that.  But, it's really easy to write out a line of text that does the job and say "here, cut and paste this..."

I'm not bashing Windows... supporting it pays me well, but the help you can get from a forum like this just blows away anything you can get for Windows.

As for understanding the commands... pretty well everything has built-in help.  ***command* --help** works wonders.  Failing that, it's **man *command*** for the manual.  It does take a while to get past all the terms before you can actually understand the help.  No doubt about it, there's a learning curve.  But, it comes.

I found, at the start, way back (not that very far), that watching the 'details' of the software install screen scroll past actually helped.  If nothing else, it makes you realise just how powerful the commandline is in Linux.

---

### Post by rishi_singh on 2011-09-30
> **Idefix82 said:**
> I wouldn't recommend burying yourself in books. 

I understand what you say. No doubt, learning is done best by doing. But i would like to have a beginner level book which will give me a structured introduction to ubuntu or linux. For things outside the book, there is always google.

---

### Post by nothingspecial on 2011-09-30
Have a read of this

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by vasa1 on 2011-09-30
[http://ubuntupocketguide.com/download_main.html](http://ubuntupocketguide.com/download_main.html)
though the contents may be dated ...

---

### Post by sanderd17 on 2011-09-30
in general, there is no way to become a Linux master. Linux is just too big. 

You can become a master in databases, web servers, app development, kernel and drivers development, package management ... but not in Linux

In anyway, all those sub-domains that you can become a master in, those all use the command line. So you de need to learn the basics of the command line first, before you chose in which direction to go.

You don't need to know each command, but everyone needs the normal file-handling commands (move, copy, remove ...) and a way to get info (via the man pages).

[http://linuxcommand.org]("http://linuxcommand.org") is indeed a good place to start.

---

### Post by rishi_singh on 2011-11-08
Long time... Can anyone suggest how to begin earning linux, like how the internals work, networking, troubleshooting and do "advanced" stuff. 

I cannot keep on using linux for just basic surfing, office and stuff.

---

### Post by sanderd17 on 2011-11-09
> **rishi_singh said:**
> Long time... Can anyone suggest how to begin earning linux, like how the internals work, networking, troubleshooting and do "advanced" stuff. 

I cannot keep on using linux for just basic surfing, office and stuff.

You should first start with reading this: [http://linuxcommand.org](http://linuxcommand.org)

Once you know some commands, try installing Arch (you will encounter lots of problems, most of the problems you will encounter are documented on the Arch wiki)

After you managed to install and tweak Arch, try to install LFS (Linux From Scratch). 

If you have done this, you could be considered to be a "master in general Linux". But Linux is broader than this. You can also learn a lot about the sub-domains of Linux (like networking, computer architecture, programming ...). Those domains aren't immediately Linux by itself, but you can learn how Linux can help you with those domains.

Estimated time to achieve all this: at least a few years.

---

