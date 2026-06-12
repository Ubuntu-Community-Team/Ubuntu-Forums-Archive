---
title: "How to get from command to package?"
date: 2010-05-25
forum: General Help
---

### Post by 5010 on 2010-05-25
I use jaunty, but if there are other ways available in newer versions I'd like to know that too.
 
I'm looking for a general way of getting from a command to information about that command in 2 environments.
 
1. GUI: Let's say I know a menu item that launches an application. How do I find out what package created it? Knowing the package, how do I find out where it organized the configs and paths related to it? I can get the launch command by consulting the menu manager. I can get info about the package by consulting synaptic. But how do I get from command to package name? And is there an easier way or plans to make an easier way? Wouldn't it be nice to right click a menu item and have an "info" pop-up that told me the package name related to a menu item? Better yet, when selecting an "info" pop-up, a "more" button to pull up details about that package? Are the mad menu scientists brewing such a magic potion for the future?
 
2. Terminal: Let's say I know a command. How do I find out what package installed that command? And knowing the package name, what is that magic syntax for dpkg that gives me the paths where the install vomitted it's configs and related junk all over the system?
 
Knowing this would make it so much easier for me to form a deeper and more satisfying relationship with my system \\:D/ OK... maybe not, but at least I would be able to figure out where stuff is organised...

---

### Post by Ozymandias_117 on 2010-05-25
There may be a more efficient way, but if you have the name of the program (What you get from the menu information) and copy that into the quick search of Synaptic Package Manager, find it, right click "Properties" and click on the "Installed Files" tab and you can see what it put where.

Edit: Forgot about your other question; dpkg is for installing .debs you have. If you want information about one of them you can use ```
dpkg -I package.deb
```. 
All the programs you've downloaded through apt (which is apt-get, aptitude, software center and synaptic package manager) are stored in /var/cache/apt/archives/

---

### Post by BoneKracker on 2010-05-25
I don't use Ubuntu and know nothing about Debian's package management system, but I guarantee you there is a way to query the package management system to find out which package owns a particular file.

Every "command" is a file.  Every menu option executes some command.  You can use the menu management application to see what command a menu executes.

To query the package management system about a command, you probably have to know it's filename including the full path.  So, how do figure that out?  Given that you know a command (whether your need originated in the graphical menu environment or at the command line), you can find out explicitly where that file is on disk by using 'which'.

Let's say you want to know which package installed the command 'kbdrate':
```
~ $ which kbdrate
/usr/bin/kbdrate
```
Then you'd query your package management system to find out which package owns /usr/bin/kbdrate.  How exactly you do that you'll have to find out from an Ubuntu or Debian user, or you'll have to find in the documentation for your package management system (if you don't know where else to go, I'd start with the man pages or info pages for 'apt' and 'dpkg'.

Modern package management systems also often have the ability to list for you all files installed by a package.  Again, consult the documentation for your package manager.

Finally, if you want general information about what a command does and how to use it, consult the man pages.  Start with:
```
man -k <command>
```That will list for you all man pages that the system thinks might have something to do with it.  From there you can be more selective.```
man <command>
```or```
man <section number> <command>
```(sometimes a "command" might exist in more than one section of the manuals -- for example, it might be a C keyword as well as the name of a gnu user utility -- so you select the section by adding the number, which you determined by looking at the list provided by 'man -k').

As already noted by someone else, you can get a general description of a package from the package management system.  That capability is also available to you in the graphical package management tools.

Finally, you can always search the web for information.

---

### Post by oldos2er on 2010-05-25
```
apt-cache search <command>
``` or ```
apt-cache search <menu item>
```

Once you know the package name, ```
dpkg -L <package name>
``` will give you details about where each file in the package is installed.

If you want a GUI, all this is available in Synaptic.

---

### Post by 5010 on 2010-05-26
Thanks for the help!  I pasted the advice to a text document and saved to my desktop so I won't forget.  

Now I am browsing around the main menu manager and finding everything behind the scenes for my apps.  Doing this in terminal via apt-cache and dpkg -L is actually quicker than pulling up synaptic.  The advice on which and man is appreciated too.

I don't recognise the stuff in /var/cache/apt/archives/ but even so the other help is getting me what I need.

Thanks again!!!!!!!

---

### Post by BoneKracker on 2010-05-26
You're welcome.

One related thing I forgot.  The 'whatis' command.  It will try to look up a brief description of a command in the man database (if you don't want to see the whole page).

Whatis tries to give a brief description of a command (from the man pages).

Sometimes 'man -k' (which also provides a brief description) casts a pretty wide net.  For example```
~ $ man -k ls |wc -l
836
```
'man -k' returns 836 entries it thinks have something to do with the 'ls' command.  But 'whatis' gives us what we want:
```
~ $ whatis ls
ls []                (1)  - list directory contents
ls []                (1p)  - list directory contents
```

There's also a man page for man, which is worth looking at:
```
~$ man man
```

---

