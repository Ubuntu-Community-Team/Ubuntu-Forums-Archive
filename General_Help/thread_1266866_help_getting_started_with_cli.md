---
title: "help getting started with cli"
date: 2009-09-15
forum: General Help
---

### Post by RFXCasey on 2009-09-15
Hey guys, I'm just getting started with Ubuntu server edition and I want to force myself to use the cli. I'm having some trouble though as I really have no clue as to what I am doing. I know a few basic commands but I can't even tell what's installed on thins machine except to look through the /etc or /bin dir and I don't know what half of that stuff it. Is there anything like the old Xtree program to make navigation a little easier but without all the fluff of a full blown desktop environment. I don't even know if I have IPtables installed. I might install gnome or kde just for convenience once in a while but I really wanna take the masochistic route and torture myself of the cli. I have heard legend of a program called midnight commander, it this good?

---

### Post by muteXe on 2009-09-15
[http://www.google.co.uk/search?hl=en&q=linux+command+line+tutorials&meta=](http://www.google.co.uk/search?hl=en&q=linux+command+line+tutorials&meta=)

---

### Post by jondkent on 2009-09-15
> **RFXCasey said:**
> I have heard legend of a program called midnight commander, it this good?
This is OK, if you like that sort of thing, but if you really are into torturing yourself, the cli is the best route, maybe with screen (*man screen*).

Don't forget CTRL-ALT-F[1-9] to access additional consoles.

Ubuntu has loads of really good guides.  The best route to learn is to have an idea of what you want to do and run with that first and build upon that.

Have fun.

---

### Post by sedawk on 2009-09-15
The most valuable time I might have ever spend for learning
Unix was reading a 2 volume manual containing all user commands
from page to page reading the summary for every command.

These pages are also available on the command line. The
man pages are divided into different sections, you
might be most interested in section 1, user commands,
and section 8, admin commands.

Read about the sections yourself (press "q" to quit)
```

man 1 intro
man 8 intro

```
( Other sections of interest might be 4 and 5)

Here is a (silly?) command to list all available user commands
of section 1 starting with an a:

```

man -k a|grep ^a|grep "(1)"|more

```
(
 "man -k a" list all man pages containing an a.
 "grep ^a" only passes on lines starting with an a.
 "grep "(1)" only passes on lines containing (1).
 "more" is a pager to stop scrolling if there are too many lines.
)

After that, all you need is some hands-on experience ...

---

### Post by scorp123 on 2009-09-15
> **RFXCasey said:**
> I'm having some trouble though as I really have no clue as to what I am doing. Ask the system: **apropos**

Let's suppose you wanted to do something that has to do with packages ... but you don't know exactly what and how. So you'd ask:
```
apropos package
```

The system will then spit out all commands that it knows that have to do with this topic and give a brief explanation.

Example:
```
> apropos package

apt (8)              - Advanced Package Tool
apt-cache (8)        - APT package handling utility - cache manipulator
apt-extracttemplates (1) - Utility to extract DebConf config and templates fr...
apt-get (8)          - APT package handling utility - command-line interface
apt-mark (8)         - mark/unmark a package as being automatically-installed
apt-sortpkgs (1)     - Utility to sort package index files
aptitude (8)         - high-level interface to the package manager
apturl (8)           - graphical apt-protocol interpreting package installer
deb (5)              - Debian binary package format
deb-control (5)      - Debian packages' master control file format
deb-old (5)          - old style Debian binary package format
deb-triggers (5)     - package triggers
deb-version (5)      - Debian package version number format
...
```

Those numbers in brackets are chapter numbers of the "man" pages. I think someone already explained that.

So to lookup the exact syntax of a command you'd do e.g.
```
man 8 apt
```

The reason for those chapter numbers is that sometimes there are two commands or libraries that might have the same name but a different meaning. Hence why it might be a good idea to always add the chapter number to make sure you get the correct page.

> **RFXCasey said:**
>  I can't even tell what's installed on thins machine ```
dpkg -l '*' | grep ii | more
```

---

### Post by nothingspecial on 2009-09-15
If you want to learn to use command line apps my advice would be to use dvtm

It`a a tiling window manager for the shell

You launch it then press Ctrl+G then C.

Now you`ve got two windows, you can even switch between them with a mouse.

Now in one sceen, type man dvtm and have a mess about, managing windows. Once you`re done with that install midnight commander.
```

sudo apt-get install mc
```

launch it in one screen and and create another one (Ctrl+G then C).

In that one type man mc.

Now you`re getting used to 2 command line apps and you have both instruction manuals there, right infront of you, while you do it.

Cool isn`t it.

---

### Post by RFXCasey on 2009-09-15
> **nothingspecial said:**
> If you want to learn to use command line apps my advice would be to use dvtm

It`a a tiling window manager for the shell

You launch it then press Ctrl+G then C.

Now you`ve got two windows, you can even switch between them with a mouse.

Now in one sceen, type man dvtm and have a mess about, managing windows. Once you`re done with that install midnight commander.
```

sudo apt-get install mc
```

launch it in one screen and and create another one (Ctrl+G then C).

In that one type man mc.

Now you`re getting used to 2 command line apps and you have both instruction manuals there, right infront of you, while you do it.

Cool isn`t it.

Um I was able to download dvtm and I can start a single window by typing dvtm at the command prompt but your whole ctrl + g the c thing doesn't do anything for me. What be the issue? The midnight commander rocks. Very Xtree esc.

---

### Post by nothingspecial on 2009-09-15
Ctrl G is the escape for dvtm. It tells the shell that the next key you press is an instruction to dvtm and not to be displayed after the prompt.

Ctrl + G at the same time, then c and you should have two windows side by side both with a prompt.

---

### Post by RFXCasey on 2009-09-15
Ah, I see, sorry too much speed reading. I did SSH into my server from putty on my desktop last night which was so kool. Does anyone know how to change the default text color in BASH? I would also like to know if there is an easy way to securely remote to a gnome desktop. Now I need to figure out how to set up some sort of secure FTP like VSFTP and host my website with apache, unless you all can suggest something better to do with my server like run a game server or something. Is it possible to run a Day of Defeat dedicated server on a linux box? Or would I learn more useful things hosting a web site or something else.

---

