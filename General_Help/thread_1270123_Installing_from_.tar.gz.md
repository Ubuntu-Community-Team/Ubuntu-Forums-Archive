---
title: "Installing from .tar.gz"
date: 2009-09-19
forum: General Help
---

### Post by sr.vinay on 2009-09-19
Help needed in installing from .tar.gz files.

---

### Post by 3rdalbum on 2009-09-19
A .tar.gz is just a compressed archive. It might contain source code, or a compiled program, or a GTK theme, or a login screen, or any other sort of computer file that you can imagine. Source code is usually compiled in one particular way, but sometimes it differs.

What instructions are given with the archive? Usually there's instructions in a file called INSTALL inside the archive.

---

### Post by TheStroj on 2009-09-19
This is a package! First you must extract it somewhere.
We can't really help you how to install it, as you didn't say much about it. 

If there is an executable file in there you just double-click it and it should run. If not, then use terminal to navigate to the folder containing the file and use ./filename command to run it.

If you have a .deb package in there, simply open it and click Install package.

---

### Post by blueridgedog on 2009-09-19
The first step is to extract it.

```
tar xvfz myfile.tar.gz
```

Will extract it in the current directory.  I recommend making a directory for extraction and moving the tar.gz file there.  From there the other posts in this thread are right...what is in in?

---

### Post by aysiu on 2009-09-19
Must you absolutely install from .tar.gz?

It's better to use the repositories if possible. More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by sr.vinay on 2009-09-27
Lol...OK. Let me re-phrase my question. I know how to extract the files from the .tar.gz file. I wanted to know how to install the *.sh file that was in it. Sorry, my question was weird! Because i tried using the "./" thing and "sh" and "source" command. None of them work!

---

### Post by sahabcse on 2009-09-27
sudo apt-get install build-essential

sudo apt-get install g++ 

tar xvfz filename.tar.gz

cd /path/to/extracted/sourcefiles
./configure
sudo make
sudo make install

---

### Post by SOLcity on 2009-09-27
> **sr.vinay said:**
> Lol...OK. Let me re-phrase my question. I know how to extract the files from the .tar.gz file. I wanted to know how to install the *.sh file that was in it. Sorry, my question was weird! Because i tried using the "./" thing and "sh" and "source" command. None of them work!
 
extract the file first then try this
 
```
 
sudo sh yourfile.sh

```

---

### Post by sr.vinay on 2009-09-27
The sudo sh thing doesn't work with all files

---

### Post by SOLcity on 2009-09-27
> **sr.vinay said:**
> The sudo sh thing doesn't work with all files
 
try to read these files (install) and (readme) I'm sure you will find your answer there

---

### Post by SuperSonic4 on 2009-09-27
the README file is always a good place to start :)

---

### Post by scouser73 on 2009-09-27
**1** - Download the .tar.gz file to **/home/username**

**2** - Right click and extract the files

**3** - Go to **System > Preferences > Main Menu**

Now you need to make a new menu item for this program, so if it's a new browser then you would make the new program in Internet.

**4** - In Main Menu, click on **New Item**

**5** - In the **Name** field you have to create a name for the program

**6** - In the **Command** field you have to navigate to the folder you have just extracted and find the program to install and select it

**7** - In the **Comment** field you can enter a comment, but it's not necessary

**8** - Now you need to select a new icon for the program


[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by Elcid247 on 2009-09-27
u could be missing on some dependencies so make sure u have all of them installed and btw most of the sites that provide files in .tar.gz format (source code) have manuals for how to compile them.


but anyway im gonna try to explain this n make this simple (which is really once u get used to it :D)

extract the files, cd to the directory

now if theres a readme present along with the code, read it; it usually will tell u what commands to execute

but let me explain some of the common ones

first off

```
sudo apt-get install build-essentials && sudo apt-get install g++
```

this installs a C++ compiler and something called make, which is like a compilation manager that the programer tells how to compile each file into executable code.

NOTE: u have to do this only once in a lifetime... u dont need it everytime u install something and it will tell u its already installed anyway :D

```
./configure
```

the "./" indicates the folder u r currently in so "./configure" is a file located in the current folder (the extracted folder). this configures the *make* utility.. sometimes found and sometimes not, but if u find a *config* or *configure* file usually run it before *make* and *make* WILL complain about it anyway if u dont do it when its needed gonna tell u no "build target specified" or something like it.

if it gives u any errors saying some library isnt found, use

```
sudo apt-get install LIBRARYNAME 
```

if that doesnt work, just fire up synaptic package manager and type the name of the missing library (look below for how to use synaptic)

```
make
```

compiles the code into executables

```
sudo make install
```

installs (copies or moves) the executables into /usr/share or /usr/bin or wherever the programer intended it to be put, as u c u need sudo cause these r write protected folders.


```
sudo make uninstall
```

yep u guessed it its just the opposite of *make install* :D aka removes executables and shortcuts---> requires all of the previous steps.


u might find an installion script in the folder, as it might seem the case with u, the script might not be executable so u might want to run

```
chmod +x INSTALLSCRIPT
```

in order to allow the execution of the script.

but dont worry not all programs on ubuntu r installed like this, this is the HARDEST way!

u could always find .deb files (like .exe just double click n ur done) in places like [getdeb]("www.getdeb.net") or installation through 
**synaptic** is even wayyyyyyyyyyyyyyyyyyyy easier! u just open it, search for the program, rightclick mark for installation then apply bam ur done :D (sometimes requires adding repositories but thats always given by the program provider so dont worry)


1 last thing, when asking for help regarding compilations from source code, post the errors u get and the program ur trying to install so we can help u even better.

good luck and welcome to ubuntu :D

---

### Post by aysiu on 2009-09-27
I'd still like to know **what** you're trying to install.

Chances are you don't need to install it from a .tar.gz

And, on the off-chance that you do, it'd be great to know what you're trying to install so people can give you more specific instructions instead of generic ones.

---

### Post by scouser73 on 2009-09-27
> **aysiu said:**
> I'd still like to know **what** you're trying to install.

Chances are you don't need to install it from a .tar.gz

And, on the off-chance that you do, it'd be great to know what you're trying to install so people can give you more specific instructions instead of generic ones.

Aysiu is correct about the installation of files of this nature as there is more than likely to be a .deb file or it's in the repositories.  Have you searched in [[COLOR="Red"]**GetDeb**[/COLOR]]("http://www.getdeb.net/") to see if the software is there?

---

### Post by sr.vinay on 2009-11-14
Thanks for the help! I knew that using Synaptic is easier and so is using a .deb file. The problem was that I couldn't figure the exact syntax to install it. Now I've got it. Thanks a lot!

---

