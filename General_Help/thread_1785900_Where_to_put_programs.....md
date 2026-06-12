---
title: "Where to put programs...."
date: 2011-06-18
forum: General Help
---

### Post by brad1138 on 2011-06-18
When "installing" a program that basically just unpacks into a directory of your making. Is there a "common" place to create the directory? I usually end up making it my home folder, but that gets crowded. 

Thanks,
Brad

---

### Post by Toz on 2011-06-18
I create a bin folder off of my home directory and put things like this in there. Its like the other bin directories (/bin, /usr/bin, etc) but for my personal executables. In fact, ~/bin (if it exists) is automatically added to your PATH so that any executable files in that directory don't need to be prefixed with ~/bin if executed from the command line.

---

### Post by mikewhatever on 2011-06-18
You can use /opt, which is empty by default.

---

### Post by brad1138 on 2011-06-18
> **Toz said:**
> I create a bin folder off of my home directory and put things like this in there. Its like the other bin directories (/bin, /usr/bin, etc) but for my personal executables. In fact, ~/bin (if it exists) is automatically added to your PATH so that any executable files in that directory don't need to be prefixed with ~/bin if executed from the command line.

Thank you, I was wondering just earlier if there was folder like that, but I didn't know how to word the question.

I have never quite understood what the bin folder was for, what does "bin" mean and/or what is it's significance. Is it just a "bin" for packages/programs?

Brad

---

### Post by Toz on 2011-06-19
I believe bin standards for "binaries", or executable programs. Linux has a default set of folders and the various bin directories are places for these executable programs.

Just did a quick search and came up with this link: [http://rute.2038bug.com/node38.html.gz#SECTION003810000000000000000]("http://rute.2038bug.com/node38.html.gz#SECTION003810000000000000000") explaining the standard filesystem setup.

---

### Post by brad1138 on 2011-06-19
> **Toz said:**
> I believe bin standards for "binaries", or executable programs. Linux has a default set of folders and the various bin directories are places for these executable programs.

Just did a quick search and came up with this link: [http://rute.2038bug.com/node38.html.gz#SECTION003810000000000000000]("http://rute.2038bug.com/node38.html.gz#SECTION003810000000000000000") explaining the standard filesystem setup.

Thanks, binaries makes sense. 

Brad

---

### Post by dFlyer on 2011-06-19
Place the programs in /opt

---

### Post by Toz on 2011-06-19
I agree that for multi-user programs, /opt is where they should be go. For personal-use binaries, ~/bin is the place. I got the impression that the OP was talking about personal-use binaries.

---

### Post by brad1138 on 2011-06-20
> **Toz said:**
> I agree that for multi-user programs, /opt is where they should be go. For personal-use binaries, ~/bin is the place. I got the impression that the OP was talking about personal-use binaries.

Correct

---

### Post by hamidszaidi on 2011-06-20
> **brad1138 said:**
> When "installing" a program that basically just unpacks into a directory of your making. Is there a "common" place to create the directory? I usually end up making it my home folder, but that gets crowded. 
 
Thanks,
Brad
 
How  & when can we choose a directory for installing a program in. using command line apt-get install or usin UBUNtu software centre

---

### Post by dusanyu on 2011-06-20
Placement of files in a Linux system is governed by [File system Hierarchy Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

the standard install locations for programs installed by a Shell script is /usr/local witch contains Tertiary hierarchy for local data, specific to a specific host system and typically has further subdirectories. for example the doom 3 installer defaults to /usr/local/games/doom3 

/opt is for Optional application software package, A package placing files in the /opt/ directory creates a directory bearing the same name as the package. This directory in turn holds files that otherwise would be scattered throughout the file system, giving the system administrator an easy way to determine the role of each file within a particular package. 

as far as selecting install directories for apt packages you cant


oh and a nice way to to keep clutter free if installing apps in your home directory is to create a /home/user/bin directory and place those programs in there.

---

### Post by hamidszaidi on 2011-06-20
> **dusanyu said:**
>  
 
oh and a nice way to to keep clutter free if installing apps in your home directory is to create a /home/user/bin directory and place those programs in there.
 
Can you elaborate the steps for in the home/usr/bin directory

---

### Post by Toz on 2011-06-20
Quite simple, actually. 

Create a bin directory in your home directory using the file manager, or via command line:```
mkdir ~/bin
```

And put your personal-use binaries in that directory.

---

### Post by brad1138 on 2011-06-20
> **Toz said:**
> Quite simple, actually. 

Create a bin directory in your home directory using the file manager, or via command line:```
mkdir ~/bin
```

And put your personal-use binaries in that directory.

You can also just select "file" and "create folder" in your home dir, (from the nautilus drop down) and name it bin

---

### Post by dusanyu on 2011-06-23
or just create a /bin directory in your home directory with nautilus :)

---

