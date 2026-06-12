---
title: "I need help with basic stuff"
date: 2009-11-17
forum: General Help
---

### Post by ikislav on 2009-11-17
Hello... I am completely new to Linux and Ubuntu and I need help.

I was a Windows user for 12 years, so you can imagine what I'm going through right now. Everything seams so strange to me in Linux... File system, program locations, settings, philosophy...

1st: Where are installed programs actually located in the file system structure? I got the impression that they can be spread out through entire file system tree. How can I find all files belonging to a particular program and all the libraries those programs depend on.

2nd: I read about how VI text editor is present in every Linux or Unix implementation. I am able to invoke VI editor with typing "VI" in the terminal window. I found VI file (a shortcut?) in /usr/bin that points to another shortcut named VI located in /etc/alternatives/vi which points to a file in /usr/bin named vim.basic. I mean... WHAT? Why this. Is the reason for this to be able to invoke VI by typing "vi" in terminal? If so, what folders are the ones that are searched for commands when I type them in terminal (without actually being at their location). There is also a shortcut called vim in /usr/bin which points to vim in etc/alternatives, which points to vim.basic in /usr/bin.

---

### Post by SeanBlader on 2009-11-17
I can help a little bit on both.

1. Basically you don't worry about where all the files for each application go, you let the package manager deal with it. Also this stems from a different philosophy in Linux than in Windows. In Linux there's far less duplicate code compared to Windows. In Windows, as a programmer, you have basic libraries that let you do a few interface things so stuff looks similar across programs, but you still do a TON of code for your application that a TON of other applications have done the same thing for, like loading a splash screen, lots of apps have them, they all have to write code to generate it and tell it when to turn off, but in Linux, there's a library for that, it's open source, no one bothers duplicating it, so everyone uses the existing on that's already on every system. Which explains why apps are ALL OVER THE PLACE. You just have to get used to the idea that apps aren't self contained little folders. This is a disadvantage for organizing, but it's a huge advantage in developer time, disk space, and more importantly memory space. This is why Windows requires so much memory to run, and you can really get by with less than 1/5th of the RAM while getting the same things done on Linux.

2. As for vi I have to admit I don't use it. Usually there are newer and more intuitive applications available, especially for someone coming from windows. gedit replaces Windows Notepad, and nano replaces DOS Edit. But eventually I will figure out and start using vi, and here's how to get started: [http://www.linfo.org/vi/index.html](http://www.linfo.org/vi/index.html)

---

### Post by ikislav on 2009-11-17
Thank you, this opens my mind a bit.

---

### Post by fancypiper on 2009-11-17
One of the best and most thorough explanation of Linux I have found is the [Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz).

To Linux, everything is in a filesystem: [The Linux filesystem explained]("http://www.freeos.com/articles/3102/")

Try this command in the terminal to find out what directories are searched for commands:

echo -e ${PATH//:/\\n}

I alias that command (you can make your own commands in Linux!) to "path".

Welcome to and enjoy this logical operating system with tons of power.  I'm finally serving my own web space!

---

### Post by P4man on 2009-11-17
You can find a detailed explanation of the filesystem hierarchy here:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

As the above poster pointed out, you typically dont really care where the apps go. If you ever need to locate the binary you can use 
```
whereis filename
```

 What you do want to learn and understand is what / (root) is, the difference between / and /root and the logic behind home folders and mount points. Took me a while to get my head around that switching from windows, but once you understand it suddenly it becomes a whole lot more logical than the windows hierarchy.

What you see about vi, you pretty much got it right. The reason for it is compatibility. I dont know the exact details, but the idea is that you can execute a program (like VI in your example) and if its not on the system, the link may point to an alternative app that does the same thing. You type in "vi" and the shell starts VIM (VI Improved). Other distributions may include different "vi" clones, but you can always type vi in a console to get some vi variant.

Anyway good luck learning vi. I know die hards swear by it, and Im sure its very powerful once you spent a year learning it, but if you're like me, you will appreciate simpler alternative text editors like gedit as graphical editor (bit like notepad) and nano if you need a terminal based text editor. But as you rightly pointed out, nano is not standard on all distributions, and vi is as old as linux (older in fact) and can be found on any linux or unix distribution.

---

### Post by Aearenda on 2009-11-17
To get the best of vi(m) on Karmic with colour coding and all you should install 'vim' otherwise all you have is vim-tiny.

---

### Post by nothingspecial on 2009-11-17
> **Aearenda said:**
> To get the best of vi(m) on Karmic with colour coding and all you should install 'vim' otherwise all you have is vim-tiny.

But I`d echo P4man and go with nano for text editing in the shell and gedit for everything else.

******Cue the vi(m) army******

---

### Post by ikislav on 2009-11-17
Wow... very helpful... I would never expect this kind of support from Windows users...

---

### Post by ikislav on 2009-11-17
> **fancypiper said:**
> One of the best and most thorough explanation of Linux I have found is the [Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz").

Thank you fancypiper, this book is absolutely fantastic, I'm reading it right now :)

---

### Post by ikislav on 2009-11-17
One more small thing... Is there a way to make terminal window remember it's position and size setting?

---

### Post by The Cog on 2009-11-17
As for your chain of links to vi - /usr/bin is the normal place for program launchers. But in the case of vi, there are multiple versions that might be installed - tiny and full for starters. So you really need a link from /usr/bin/vi to the real program, whichever one it is that you want to run. But the normal place to store system configuration such as which version to default to is in /etc, and in fact /etc/alternatives is full of links to the preferred alternative program. Backing up /etc backs up pretty-much all of your system config, including which alternative you prefer. So in practice, /usr/bin/vi links to /etc/alternatives/vi which is configured to link to your preferred alternative version of vi.

Vi is kind of strange to use. I made the effort to memorise just enough to be able to edit a config file to get myself out of trouble many years ago, and that has paid off over the years. But I wouldn't choose to use it except for only the smallest of changes or if my preferred GUI editors were broken.

---

### Post by fluffman86 on 2009-11-17
to set the size, click terminal, then select the size you want.  it can't remember it's position, though.  

Also, 80x24 is default for a reason: a lot of older programs display best when things are set for 80 characters wide.  It won't matter most of the time, though.

And while I'm at it, I might as well join in on the vi debate.  I don't really care much for vi or vim-tiny, but once you
sudo apt-get install vim

you get all sorts of fancy text highlighting.  You should definitely read into vim more.  It's super powerful.  It even includes a very helpful tutor.  Just open a terminal and type "vimtutor" and it will walk you though how to do a lot of basic stuff.

The most important things to remember though:
i = insert, for editing.
Esc = stop whatever you were doing, like editing.
:q = colon issues a command, q is for quit, when you haven't made changes.
:q! = quit, and DO NOT SAVE
:wq = write the file, then quit.  ZZ (without the colon) will do the same.

And some neat tricks:
dw = delete a word
dd = delete a line
d4w = delete 4 words (replacing 4 with any number, like 999)
d4d = delete 4 lines.
/searchterm = searches for the word searchterm, then use n or N to search for next/previous
h,j,k,l = navigation, so you don't have to use the arrowkeys.

It's so cool. :D

---

### Post by QLee on 2009-11-17
[QUOTE=ikislav]One more small thing... Is there a way to make terminal window remember it's position and size setting?[/QUOTE]

I not absolutely sure what you are trying to accomplish. However, if you start the xterm with a "-geometry" option, you can specify both size and screen location, that might be what you want.

---

### Post by oldos2er on 2009-11-17
"How can I find all files belonging to a particular program and all the libraries those programs depend on."

 To find where each file in a package has been installed, run **dpkg -L <package name>**

**apt-cache show <package name>** will show dependencies, and other information.

 If you prefer a GUI to do these tasks, use Synaptic Package Manager.

---

