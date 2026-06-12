---
title: "New to ubuntu. Easy Beginner Question"
date: 2010-07-16
forum: General Help
---

### Post by Mike_30 on 2010-07-16
I have used several version of Linux over the past few years off and on as well as Windows. (mainly use windows because of work)

I just started on Ubuntu 10 after a buddy told me about it. Now for my silly question.

I noticed when installing some programs they dont go into the Apps, Places, or System categories. Where do they go? For example I tried to install a .Rar opening program and it said it installed but I have no idea where it went...

Thanks

---

### Post by cavalier911 on 2010-07-16
In most cases a program with no GUI has no menu entry.

The program must be run from terminal if it has no GUI.

An executable could be installed in any location listed in

```
echo $PATH
```

most are installed in /usr/bin or /usr/sbin .

Open terminal

```
man rar
```

```
rar -?
```

---

### Post by lordskid on 2010-07-16
Did you install it through synaptics? or did you compile code?

---

### Post by oomar on 2010-07-16
you installed a rar opening program? did you just install rar support for ubuntu's defaul archive manager? if so then there wouldnt be another program to find.

---

### Post by Bradj47 on 2010-07-16
You can see where the executable of any program is located by typing ```
which <name of command>
``` So in this case you would type ```
which rar
``` and you should get a path to where it installed, at least if it's in your $PATH like a previous user suggested.

---

### Post by Mike_30 on 2010-07-17
I downloaded it using ubuntu software center in 10.4 64 bit.....

I guess I am not paying attention to what program has a GUI and which is ran through terminal. Is there any way to see that before I install? or am I not paying attention.

I think I may need a book on commands.............any recommendations?

I remember some basic ones but the rest I have to google.

---

### Post by neoargon on 2010-07-17
> **Mike_30 said:**
> I downloaded it using ubuntu software center in 10.4 64 bit.....

I guess I am not paying attention to what program has a GUI and which is ran through terminal. Is there any way to see that before I install? or am I not paying attention.

I think I may need a book on commands.............any recommendations?

I remember some basic ones but the rest I have to google.
Do you remember the name of the application?
If what you installed was something to add the functionality to existing extractor,(naturally) since it is not an application, it won't show up in  "applications" . What you installed will be most probably "unrar" . Just check it

And I don't think there is any need of knowledge in commands needed to use ubuntu(my experience)

---

### Post by Bradj47 on 2010-07-17
> **Mike_30 said:**
> I downloaded it using ubuntu software center in 10.4 64 bit.....

I guess I am not paying attention to what program has a GUI and which is ran through terminal. Is there any way to see that before I install? or am I not paying attention.

I think I may need a book on commands.............any recommendations?

I remember some basic ones but the rest I have to google.

This looks promising: [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

Remember all Unix operating systems come with manuals on their commands. These are known as man pages. To open up a man page just type ```
man command
``` That example would open a man page on the command command, if there were such a command. :P

On most man pages there's a helpful SEE ALSO section at the bottom that tells you about similar commands that may be useful to you. 

For starters, try doing a man on **apt-get**. So you would type ```
man apt-get
``` You might find it faster to just type a command to install packages than go through the software center. 

And welcome to Ubuntu! :D

---

### Post by UltraZone on 2010-07-17
For a pretty complete description of command line interface commands bookmark this site:

[http://ss64.com/index.html](http://ss64.com/index.html)

look under the Bash section.  They cross-reference functionality with semi-equivalent windows CMD commands.

---

