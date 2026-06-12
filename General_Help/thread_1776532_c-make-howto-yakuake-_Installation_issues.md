---
title: "c-make-howto-yakuake-? Installation issues"
date: 2011-06-06
forum: General Help
---

### Post by 3xp10r3r|X13 on 2011-06-06
Hello there,
I'm just having a little newbie issue concerning the installation of yakuake using a tar.bz2 file.

Unfortunately I couldn't find any installation guides, because lots of people or rather most people are simply installing it, using a deb. Package. (Using Slackware at the moment, so I'm not able to do it that way)

The extracted file doesn't contain a "config" or "setup" file I could run, but a "doinstall-sh" file and a very useful README document.
It says the following:

1. tar xfvj yakuake-<version>.tar.bz2
2. cd yakuake-<version>
3. mkdir build
4. cd build
5. cmake -DCMAKE_INSTALL_PREFIX=<path to install to> ../
6. make
7. sudo make install

So this is actually not a problem, but I don't really know how to handle C-make (not used to the GUI of it as well)

The thing I want to know is:
How to run the cmake command (where do I have to enter the path I want to install it to? what does the "../" thing mean?

tried:

when I enter the path "/usr/share" into the tags it tells me: bash: ../: Is a directory

Any suggestions are very welcome :)

---

### Post by seawolf167 on 2011-06-06
For *cmake* it looks like you need to install that package first before you can use it

```
sudo apt-get install cmake
```

then you'll be able to run the command in line #5

As for the ../ this means "parent directory", so in line #5 it looks as if it is setting the the install prefix as the name of the parent directory (i.e. the one you cd to in step 4)

---

### Post by 3xp10r3r|X13 on 2011-06-06
First of all, 
Thanks for your reply, but unfortunately that is not the problem. C-make is already installed (even the GUI for it). I just don't know how to use the c-make command related to this installation.

---

### Post by seawolf167 on 2011-06-06
> **3xp10r3r|X13 said:**
> C-make is already installed (even the GUI for it). I just don't know how to use the c-make command related to this installation.


> **3xp10r3r|X13 said:**
> cmake -DCMAKE_INSTALL_PREFIX=<path to install to> ../

Modify the <path to install to> to your installation location

i.e. if you want to install to /home/*yourusername*/*somefoldername* you would change that line to read

```
cmake -DCMAKE_INSTALL_PREFIX=/home/*yourusername*/*somefoldername* ../
```I've never used cmake before, so double check the readme file for the correct line (I'm not sure about the proper syntax for cmake specifically regarding the ../ at the end). You can also read the man page for *cmake* and see if anything is there 

```
man cmake
```

---

### Post by 3xp10r3r|X13 on 2011-06-06
all right, 
I've installed the whole thing, but into the build folder, it told me to create...
How can I install it sot everything is getting installed into the right directory, because now I'm having folders like bin and share, icons etc. in that build folder?

---

### Post by seawolf167 on 2011-06-06
I hate to say this but take another look at the readme, it may provide some more info.

If it doesn't, then the install path is up to you, i.e., maybe drop the binary in /usr/bin (somewhere in your $PATH variable) and link it to the installed folder?

Else you can run it by doing

```
cd /path/to/installed/location
./programname
```

---

### Post by 3xp10r3r|X13 on 2011-06-06
Says nothing more in the read me file..

However, thanks for your help; you pretty much solved the problem for me.(I was typing the path within the tags: </whatever/path> - that caused the actual problem and I just didn't think of it...idiot - luckily you learn out of mistakes :) )

---

