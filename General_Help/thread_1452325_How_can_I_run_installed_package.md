---
title: "How can I run installed package?"
date: 2010-04-11
forum: General Help
---

### Post by lkjhgfd on 2010-04-11
I am running the xfce desktop on a new ubuntu 9.10 installation.  I used the Synaptics Package Manager to install several applications, including R, the statistics programming language.  After the installation, it took me quite a while to find where the package manager put the executable, but I found it.  The problem is, I can't figure out how to get it to execute.  I tried double clicking on it and I tried right clicking on it and selecting "Execute" from the menu that pops up.  I really want to love ubuntu, but it's not easy for me right now.  

How do I get an executable to execute?  Also, is there an easy way to track down where the executables get put after I use the Synaptics Package Manager?  It would be handy if I could put links to them in some central location.  Thanks in advance for any helpful advice.

---

### Post by SoulMazer on 2010-04-11
To execute file 'MyFile' in directory '/home/foo/Documents/', do the following:

```
cd /home/foo/Documents/
chmod 755 MyFile
./MyFile
```

That should run it.

As for your second question, a pretty reliable way to find it is to look at the name of the package your installing. Then, open up a terminal and type in the following command:
```
whereis PackageName
```

Post back if you need any more help.

---

### Post by pbrane on 2010-04-11
In Synaptic Package Manager you can also find out what directories files have been installed to by highlighting the package and clicking on the *Properties* button. Or right-click and select *Properties*. Look under the *Installed Files* tab.
As SoulMazer pointed out a quicker way to find the executable is with *whereis*. You can also use **which *command***, this will only list the executable. Where *command* is the name of the executable you want to find.

I'm pretty sure you run **R** in a terminal.
```

$ R

```

---

### Post by jdackle on 2010-04-11
What pbrane said for the Synaptic package manager can also be done in a terminal with dpkg:
```
dpkg -L <package-name>
```Do NOT include the version information (anything after the first hyphen: **-**

If you are unsure about what the exact package name is, run:
```
dpkg -l <*some-part-of-the-package-name-you're-sure-is-in-its-name*>
```Do note the ***** wildcard before and after anything else. ;)

NOTE: Both Synaptic and dpkg only provide this information for installed packages. You can use apt-cache or apt-file for uninstalled packages. ;)

---

### Post by lkjhgfd on 2010-04-12
Thanks to all who responded.  I appreciate the tips on finding stuff.   But ultimately, I can't get R to run. 

> ls -all 

returned

-rwxr-x-r-x 1 root root 5476 2009-10-16 22:00 R

which I understand means that it everyone can read or execute it, but only root can write it.  But that was a logical place to start.  I tried running it in the terminal and got a message that it can't find a file, libR.so.  

> whereis libR.so was able to find it, so I'm guessing that it isn't in the directory where R expects it to be.

I need R, and I don't have time to mess with this.  So for now, I'm stuck with the Windows version, which works fine.  I'll come  back to trying to get it to work here when I have some free time.  It will be fun.

Thanks again.

---

### Post by jdackle on 2010-04-12
1. Your read of the results of ls -all is correct. :)


2. Maybe this is useless, maybe it's useful: I recall when I installed R a few years ago (just curious then, I use PSPP for statistics), I had to install severall CPAN packages too... :-?
I installed it following a tip in a thread (that was sticky then but I can't remember on which board, the Desktop one maybe?) I actually found by looking for "graphical R" - try it. The thread is old but may still help. ;)

3. Also, I hadn't noticed this before:
> **lkjhgfd said:**
> It would be handy if I could put links to them in some central location.Well, besides your XFCE menu (on which you won't find the console-based R but will find its GUI if installed), the PATH system variable works just like in DOS/Windows:```
echo $PATH
```Folders where Linux will look for executables are separated by **:**.
You can also add new folders to it:```
PATH=$PATH<:new_folder:new_folder#2>
```

---

