---
title: "Clamav - where is it?"
date: 2010-02-18
forum: General Help
---

### Post by boosterjet on 2010-02-18
Just installed Clamav from synaptic, what happens now? Is there a access somewhere to run a scan or log viewer, can't find it anywhere. Running 9.10.

---

### Post by dcstar on 2010-02-18
> **boosterjet said:**
> Just installed Clamav from synaptic, what happens now? Is there a access somewhere to run a scan or log viewer, can't find it anywhere. Running 9.10.

It is a command line program, look at the man page or install the GUI front end.

---

### Post by boosterjet on 2010-02-18
Sorry, but that means nothing to me, what's the man page? What is GUI front end? 
This is supposed to be better/easier than Windows ?? Sheesh!

---

### Post by lisati on 2010-02-18
> **boosterjet said:**
> Sorry, but that means nothing to me, what's the man page? What is GUI front end? 
This is supposed to be better/easier than Windows ?? Sheesh!

The "man page" is something you look at on the command line. From Applicatopms->accessories-terminal, type in:
```
man clamav
```

A GUI is "Graphical user interface".

---

### Post by jocko on 2010-02-18
> **boosterjet said:**
> Sorry, but that means nothing to me, what's the man page?A man page is a manual for how to use a program. 
To see the clamav's man page, type:
```
man clamav
```in a terminal. Scroll the text in the terminal with your mouse or the up/down arrow keys, quit by pressing "q".
> **boosterjet said:**
> What is GUI front end?A GUI is a **G**raphical **U**ser **I**nterface, so a GUI front end is a graphical application that controls a program that is otherwise terminal based. The package "clamtk" provides a GUI for clamav, so either find it in synaptic (System-->Administration-->Synaptic package manager) or run this in a terminal:```
sudo apt-get install clamtk
```> **boosterjet said:**
> This is supposed to be better/easier than Windows ?? Sheesh!That's a matter of personal preference and habit. If you are used to windows, starting with linux may be confusing and look difficult at first, but most of that is because in linux you don't do things exactly the same way as you do them in windows.

One thing you have probably noticed is that when you look for help here or on other websites, most of the time there are terminal commands instead of a description on how to use a graphical program to accomplish the same thing.
This does not mean that there are no graphical programs to do those things, it's just that it's usually easier to answer questions in forums by typing "run this in a terminal" (followed by one or a few lines of commands) than "Open this program (+some path in the gnome menu system), click this, then that, then browse there, type this, click that button, check that checkbox, click `apply`, click `exit`"...

Another thing that is different in linux is that **there are no viruses** in the wild that infects linux systems, so you have no need for an antivirus program unless you want to scan a windows partition or if you run a mail server or perhaps if you have a mixed linux/windows home network. Or if you are just a little bit paranoid.

---

### Post by 3rdalbum on 2010-02-18
It's so much easier than Windows, you don't even need to bother with a virus scanner.

Have a nice day.

(but for future reference, some programs are graphical programs that are run from the menu, some are command-line programs that can only be run by opening a terminal, and some are "daemons" which run automatically on startup and as such don't go into your menu. Unless you're an experienced user, you won't want to bother with the command-line programs).

---

### Post by donato roque on 2010-02-18
This thread might help you.  [Ubuntu Forum]("http://ubuntuforums.org/showthread.php?t=1407053")

This Ubuntu Community Documentation for [Clamav]("https://help.ubuntu.com/community/ClamAV") can also shed some light.

---

### Post by boosterjet on 2010-02-18
Well, I just uninstalled the whole damn shooting match. Problem solved ?? I haven't had to use command lines since I had to dos:\ word perfect . Still a great word processor.

---

