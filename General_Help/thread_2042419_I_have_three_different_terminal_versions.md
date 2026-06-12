---
title: "I have three different terminal versions"
date: 2012-08-14
forum: General Help
---

### Post by RedRat on 2012-08-14
I recently made a virgin install of 12.04LTS on my HP machine--no other OS is present other than Ubuntu. I note that I now have three different "Terminals" installed. This is running Gnome Classic.

Terminal 1. Applications>Accessories>Terminal
Terminal 2. Applications>System Tools>UXTerm
Terminal 3. Applications>System Tools>XTerm

Now all of these have slightly different properties. For example, I had installed on my Desktop a file called "tmp" which is was locked (little lock symbol), I was not the owner. When I opened the standard Terminal (Terminal 1 above) and cd to Desktop and put in the command 'ls' it did not show the 'tmp' folder, however both Terminal 2 and Terminal 3 did show it. There were some other slight differences.

What gives with each of these terminals??? How can you make them show all folders regardless of who owns them? 

BTW, I got the "tmp" folder while attempting to install a Lexmark driver. I got outstanding help from the folks at Lexmark in finally getting the driver installed and shout-out to their Linux person! Very impressed in getting a problematic driver installed.

---

### Post by ads52 on 2012-08-15
> **RedRat said:**
> What gives with each of these terminals??? 

There are many more to chose from:

```

andrew@corinth:~$**[COLOR="Red"] apt-cache search terminal | grep emulator[/COLOR]**
gnome-terminal - GNOME terminal emulator application
gnome-terminal-data - Data files for the GNOME terminal emulator
konsole - X terminal emulator
konsole-dbg - debugging symbols for the KDE X terminal emulator
libvte-2.90-9 - Terminal emulator widget for GTK+ 3.0 - runtime files
libvte-2.90-common - Terminal emulator widget for GTK+ 3.0 - common files
libvte-2.90-dev - Terminal emulator widget for GTK+ 3.0 - development files
libvte-2.90-doc - Terminal emulator widget for GTK+ 3.0 - documentation
libvte-common - Terminal emulator widget for GTK+ 2.x - common files
libvte-dev - Terminal emulator widget for GTK+ 2.0 - development files
libvte-doc - Terminal emulator widget for GTK+ 2.x - documentation
libvte9 - Terminal emulator widget for GTK+ 2.0 - runtime files
xterm - X terminal emulator
aterm - Afterstep XVT - a VT102 emulator for the X window system
aterm-ml - Afterstep XVT - a VT102 emulator for the X window system
evilvte - lightweight terminal emulator based on VTE
fbterm - A fast framebuffer based terminal emulator for Linux
kterm - Multi-lingual terminal emulator for X
kxterm - CERNLIB data analysis suite - KUIP terminal emulator
lxterminal - desktop independent vte-based terminal emulator
mrxvt - lightweight multi-tabbed X terminal emulator - complete version
mrxvt-cjk - lightweight multi-tabbed X terminal emulator - CJK version
mrxvt-common - lightweight multi-tabbed X terminal emulator - common files
mrxvt-mini - lightweight multi-tabbed X terminal emulator - minimalistic version
pterm - PuTTY terminal emulator
roxterm - Multi-tabbed GTK/VTE terminal emulator
rxvt - VT102 terminal emulator for the X Window System
rxvt-beta - VT102 terminal emulator for the X Window System
rxvt-ml - multi-lingual VT102 terminal emulator for the X Window System
rxvt-unicode - RXVT-like terminal emulator with Unicode support
rxvt-unicode-256color - multi-lingual terminal emulator with Unicode support for X11
rxvt-unicode-lite - RXVT-like terminal emulator with basic Unicode support
rxvt-unicode-ml - multi-lingual terminal emulator -- transitional package
s3dvt - 3d terminal emulator for s3d
sakura - simple but powerful libvte-based terminal emulator
slrnface - shows X-Faces from a newsposting on an X11 terminal emulator
stjerm - lightweight terminal emulator
termit - Simple terminal emulator based on vte library, embedded lua
tilda - terminal emulator with first person shooter console likeness
vala-terminal - Terminal emulator for mobile devices
vtprint - Prints to term emulator via ANSI codes
xfce4-terminal - Xfce terminal emulator
xfce4-terminal-dbg - Xfce terminal emulator - debugging symbols
xtel - X emulator of the French Minitel
xttitle - Changes X terminal emulator window titles
xvt - X terminal-emulator similar to xterm, but smaller
yakuake - a Quake-style terminal emulator based on KDE Konsole technology
yeahconsole - drop-down X terminal emulator wrapper
andrew@corinth:~$ 

```

Have a look at my best friend sakura :).

---

### Post by itcotbtoemik on 2012-08-15
...which doesn't answer his question.  Offhand, I'd think that the directory doesn't show up due to color differences (except that my recollection of the color schemes hints that's unlikely).  The symbol itself would be buried away in a dot-file.

---

### Post by itcotbtoemik on 2012-08-15
More likely (noticed originally as a Konsole (mis)feature), the terminal may be starting in some other directory than the user's home directory, e.g., the Desktop.  That's easily checked by using "pwd".

---

### Post by RedRat on 2012-08-15
> **itcotbtoemik said:**
> More likely (noticed originally as a Konsole (mis)feature), the terminal may be starting in some other directory than the user's home directory, e.g., the Desktop.  That's easily checked by using "pwd".


In all cases I moved to the Desktop and did 'ls'. Very definitely the "tmp" locked folder did not display AND I could not use cd to move to that directory. I got back an error that said "no such directory". However, the other terminals showed it and I could move to those terminals.

I am impressed with all the kinds of terminals that are available, but I stand by my original question: What are these extra terminals for? OK, I am coming from 8.04 and there was only one terminal and I thought that all terminals were the same. Clearly this is not the case.

---

### Post by itcotbtoemik on 2012-08-15
The reason for xterm/uxterm showing up is mentioned here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645736](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645736)

Essentially, the xterm icons show up in the menus because the safe-settings use xterm (gnome-terminal hasn't been found suitable for that purpose).

As for why the locked folders don't show up in gnome-terminal - perhaps that's a "feature" (though it would only be possible to tell if there were documentation).

---

### Post by Nardon on 2012-08-15
Xterm was the old X11 terminal emulator. Since most Linux distro's uses X11 as it's window manager, most have it installed by default. As far as I know this is just legacy software that for some reason shows up in this release (never saw them before!)

---

### Post by ads52 on 2012-08-15
> **RedRat said:**
> I am impressed with all the kinds of terminals that are available, but I stand by my original question: What are these extra terminals for? OK, I am coming from 8.04 and there was only one terminal and I thought that all terminals were the same. Clearly this is not the case.

For many users these days the only terminal emulator of any interest will be the default and even then it will be treated with some trepidation. Other terminal emulators are failed projects that have fallen by the wayside while others have been created by developers hoping to improve on old models. For terminal users the rich offering is a great thing :).

If you were interested in exploring you could do worse than explore some of the current frontrunners such as Terminator, Sakura, Guake / Yakuake and RoxTerm. Otherwise simply stick to the default if it meets your needs....

---

### Post by houseworkshy on 2012-08-15
I'd be inclined to try a "whoami" in each of the terminals.  Seeing differant things could mean differant permissions.  You could also try some admin task in each of them without prefacing with "sudo".  Any old none critical admin task, looking at the system monitor for example.  I'd want to be sure that none of them had higher privalages than they should.

---

### Post by RedRat on 2012-08-15
> **itcotbtoemik said:**
> The reason for xterm/uxterm showing up is mentioned here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645736](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645736)

Essentially, the xterm icons show up in the menus because the safe-settings use xterm (gnome-terminal hasn't been found suitable for that purpose).

As for why the locked folders don't show up in gnome-terminal - perhaps that's a "feature" (though it would only be possible to tell if there were documentation).

I went to that web site and I thank the gods of Linux that these extra two terminals were there. Using only the standard terminal that comes with 12.04, I would not have been able to chown the "tmp" folder so that I could delete it. Only these two other terminals even showed it. The funny thing is that Nautilus did not show the locked "tmp" folder but Thunar did show it. 

In theory, you could have such a locked folder created but have no way of getting to it with only the standard terminal. Perhaps there is a way to alter the properties of the standard Gnome terminal so that it showed everything and allowed me to run chown. This could be problematic in the future.

---

### Post by RedRat on 2012-08-15
> **houseworkshy said:**
> I'd be inclined to try a "whoami" in each of the terminals.  Seeing differant things could mean differant permissions.  You could also try some admin task in each of them without prefacing with "sudo".  Any old none critical admin task, looking at the system monitor for example.  I'd want to be sure that none of them had higher privalages than they should.

OK tried each one and each came back with my correct user name,i.e., issuing the whoami command. 

Clearly, some do show or have different permissions. The standard terminal (terminal 1 in my original post) did not even show the locked "tmp" file, I could not even issue the chown command with or without sudo. What became important in my original problem was actually the ability to go into that folder and make a change in a script file, lua.sh, to correct and then save the file. Once I was able to use chown recursively, I could then edit that file using gedit.

---

### Post by itcotbtoemik on 2012-08-16
> **ads52 said:**
> For many users these days the only terminal emulator of any interest will be the default and even then it will be treated with some trepidation. Other terminal emulators are failed projects that have fallen by the wayside while others have been created by developers hoping to improve on old models. For terminal users the rich offering is a great thing :).

If you were interested in exploring you could do worse than explore some of the current frontrunners such as Terminator, Sakura, Guake / Yakuake and RoxTerm. Otherwise simply stick to the default if it meets your needs....

It depends - they're *not* all the same.  xterm is the most actively-developed terminal emulator, followed by rxvt-unicode.  VTE-based terminals (notably the ones mentioned above) are fairly stagnant (noting that last year's changes were limited to compiler-warnings and tweaking the message files).  A few are inactive, most are "supported".

---

### Post by smartboyhw on 2012-08-16
> **itcotbtoemik said:**
> It depends - they're *not* all the same. xterm is the most actively-developed terminal emulator, followed by rxvt-unicode. VTE-based terminals (notably the ones mentioned above) are fairly stagnant (noting that last year's changes were limited to compiler-warnings and tweaking the message files). A few are inactive, most are "supported".
 Others are emulators, the original terminal is the best.

---

### Post by RedRat on 2012-08-17
> **smartboyhw said:**
> Others are emulators, the original terminal is the best.
It all depends on what you mean by the "original terminal". In my case, that seems to be my Terminal 1, in my original post. However, it did not show the locked folder "tmp". I actually needed to be able to "unlock" "tmp" so that I could edit a script file that had a misspelling in it--this by the helpful people at Lexmark.  By using one of the other terminals, I was able to chown the folder and then use the regular terminal actually see it and go into it and change the script file. This allowed me to install the Lexmark drivers for my printer. 

While I was inclined to remove those "extra" terminals, I now know that I must keep them about. From my experience, limited for sure, I would say that that the "original terminal" has only limited capabilities for rather simple commands. From this I would say it not the "best"--though for many it may be useful. Clearly, for a newbie, who has little or no experience with the CLI, it might keep him/her out of trouble. But if you really have to get down and dirty, one of the other terminals may be needed.

---

### Post by houseworkshy on 2012-08-24
One can also suspend the GUI and go to a terminal with +ctrl +alt +any  function key from 2 to 6 inclusive, one resumes the gui with +ctrl +alt  +F7.  Things that can be run from the command line seem to go a bit  quicker this way, virus scanning, etc.
I'm finding that I lean more and more on the terminal as the GUI's change so much.  
As to simple tasks only, well hardly.  To illustrate there is a command  called "apropos" which searches through the command line manual for  whatever word follows it.  One can use it to find commands which may  help with some particular task, very helpful for when you know what you  want to do but don't know what the command is.  So for example if one  knows that what one wants to do has something to do with networking the  word will likely be in any manual page for whatever the command is so   "apropos networking" would pull likely candidates.  One can then look at  the manual pages for those candidates eg "man netstat".  Browsing  around with those two commands gives and idea of what can be done.  The  command line can do more than the gui, graphical applications excepted. 

I get the impression that you know all the above anyway, I'm only  pipeing up for the command line in case people who don't ( apt-get is on  the outer limits of geekishness types ) get the wrong idea.  Not so  hard for newbies really, can get the basics in a couple of hours and, if  that includes how to access to the inbuilt help, can feel around for  the rest.
Unlike the fast changes in GUI's, especially irritating being the  discarded features and functionalities, where any learning quickly  becomes redundant the command line changes only very slowly.  For any  who don't like starting from scratch every few years the command line is  the thing to learn.

---

