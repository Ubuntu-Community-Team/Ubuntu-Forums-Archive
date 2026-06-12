---
title: "Cannot install from source code"
date: 2012-06-04
forum: General Help
---

### Post by unitedanarchy on 2012-06-04
For some reason I cannot install from source code, Maybe it is just the source code that I am using, But I can't install for some reason. It will say there is no make file for example, When I can see in the folder there is. I have a folder filled with source code, Mostly of games I want.

---

### Post by uylug on 2012-06-04
Do a ls -l and post the output here.

Also, you might as well try the following:

```
./configure
```

---

### Post by oldos2er on 2012-06-04
> **unitedanarchy said:**
> For some reason I cannot install from source code, Maybe it is just the source code that I am using, But I can't install for some reason. It will say there is no make file for example, When I can see in the folder there is. I have a folder filled with source code, Mostly of games I want.

Names of programs? A link to the source code would be nice too.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by unitedanarchy on 2012-06-04
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ./configure
./configure: 118: pconf/pconf: not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ 


I want you all to know I don't think it will let me compile ANY source code, Which is my I posted this. 

valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ls-l
ls-l: command not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$

---

### Post by idoitprone on 2012-06-04
> **unitedanarchy said:**
> valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ./configure
./configure: 118: pconf/pconf: not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ 


I want you all to know I don't think it will let me compile ANY source code, Which is my I posted this. 

valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ls-l
ls-l: command not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$

```
sudo apt-get install build-essential
```you need to build tools and then you have to install all the developing dependcies to compile

it not a quick process unless they listed their depencies

try```
 ./configure
``` again

you need a space between```
 ls -l
```

---

### Post by unitedanarchy on 2012-06-05
valeskagrim@ValeskaGrim:~$ sudo apt-get install build-essential
[sudo] password for valeskagrim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
valeskagrim@ValeskaGrim:~$

---

### Post by unitedanarchy on 2012-06-05
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ls -l
total 344
-rw-r--r-- 1 valeskagrim valeskagrim   251 2010-03-07 14:44 AUTHORS
-rw-r--r-- 1 valeskagrim valeskagrim 16936 2011-08-07 12:18 changelog
-rw-r--r-- 1 valeskagrim valeskagrim     2 2010-03-05 11:10 compat
-rwxr-xr-x 1 valeskagrim valeskagrim  2597 2003-12-14 00:24 configure
-rw-r--r-- 1 valeskagrim valeskagrim  1916 2010-03-05 11:10 control
-rw-r--r-- 1 valeskagrim valeskagrim   600 2010-03-05 11:10 copyright
-rwxr-xr-x 1 valeskagrim valeskagrim   145 2004-06-21 20:14 distclean
-rw-r--r-- 1 valeskagrim valeskagrim 10075 2010-03-20 16:45 HACKING
drwxr-xr-x 2 valeskagrim valeskagrim  4096 2010-06-03 17:33 include
-rw-r--r-- 1 valeskagrim valeskagrim  4004 2011-04-03 12:13 INSTALL
-rwxr--r-- 1 valeskagrim valeskagrim  1987 2011-04-03 12:11 installsardata
-rw-r--r-- 1 valeskagrim valeskagrim 15432 2001-04-05 17:59 LICENSE
-rw-r--r-- 1 valeskagrim valeskagrim   182 2010-04-27 07:55 Makefile
-rw-r--r-- 1 valeskagrim valeskagrim   213 2010-03-05 11:10 menu
drwxr-xr-x 2 valeskagrim valeskagrim  4096 2010-09-08 10:58 pconf
-rw-r--r-- 1 valeskagrim valeskagrim  1294 2010-03-05 11:10 postinst
-rw-r--r-- 1 valeskagrim valeskagrim  1090 2010-03-05 11:10 prerm
-rw-r--r-- 1 valeskagrim valeskagrim  2329 2011-08-07 12:17 README
-rw-r--r-- 1 valeskagrim valeskagrim  2810 2010-03-05 11:10 rules
drwxr-xr-x 8 valeskagrim valeskagrim 32768 2011-08-07 12:16 sar
-rw-r--r-- 1 valeskagrim valeskagrim   123 2010-03-05 11:10 SearchAndRescue.desktop
-rw-r--r-- 1 valeskagrim valeskagrim 32624 2010-09-13 15:48 SearchAndRescue.xpm
-rw-r--r-- 1 valeskagrim valeskagrim    52 2011-08-07 12:16 TODO
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$

---

### Post by Kr0nZ on 2012-06-05
> **unitedanarchy said:**
> 
-rwxr-xr-x 1 valeskagrim valeskagrim  2597 2003-12-14 00:24 configure


You need to run
./configure

Also did you read the INSTALL file?
It should say howto compile and install

---

### Post by unitedanarchy on 2012-06-05
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ./configure
./configure: 118: pconf/pconf: not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0


But again, I am just using this as an example. If you have a source you know users can compile out of the box, Give it to me, I'll try it.

---

### Post by idoitprone on 2012-06-05
> **unitedanarchy said:**
> valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ./configure
./configure: 118: pconf/pconf: not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0


But again, I am just using this as an example. If you have a source you know users can compile out of the box, Give it to me, I'll try it.

read the README and INSTALL

 libgconf2-*dev*
is probably a dependency and must be installed
It will be pretty painful to find them one by one
Please read the Readme and INSTALL or at least post it here or else we cannot help you

there is no such thing as being able to compile out of the box because all modern linux distros does not install the proper developers tools other than python

---

### Post by Toz on 2012-06-05
@unitedanarchy, 
From the INSTALL file:
```
------------------------
STEP 0: Before you Begin
------------------------

	Before you try to build and install Search and Rescue, you'll
	need to have some other packages installed first. What follows
	are a list of libraries and their package names on Debian (and
	Debian related) distributions.

	Name       -- Package name
	X11        -- libx11-6
	X11 SM     -- libsm-dev
        X11 i      -- libx1-dev
	X11 XMU    -- libxmu-dev
	SDL        -- libsdl1.2-dev (optional for sound)
	SDL Mixer  -- libsdl-mixer1.2-dev (option for sound)
	OpenGL     -- libglu1-mesa-glx libglu1-mesa-dev
	X11 ICE    -- libice6
	X11 Pixmap -- libXpm-dev

	If you find additional dependencies which are not included in your
	distribution, please report them so we can add them to the list.
```

Unfortunately, there are a couple of typos there, the final set should include:
```
sudo apt-get install libx11-6 libsm-dev libx11-dev libxmu-dev libsdl1.2-dev libsdl-mixer1.2-dev libgl1-mesa-glx libglu1-mesa-dev libice6 libxpm-dev
```

Then:
```
./configure Linux --prefix=/usr -v
```

Then:
```
make all
```

Then:
```
sudo make install
```
...(note this is different than instructions since root account is disabled by default on ubuntu)

You also need to get the data files. From the INSTALL file:
```
Next, you need to install the latest SearchAndRescue data files
	in to the directory.

		/usr/share/games/searchandrescue/

	You can obtain the latest data files at the same place where you
	obtained this source.  Once you have obtained the data files
	package, su to root as needed and type:

	# mkdir -p /usr/share/games/searchandrescue/
	# cd /usr/share/games/searchandrescue/
	# tar -zxvf /home/me/SearchAndRescue-data-1.3.0.tar.gz

	Alternitively, if you have the SearchAndRescue-data-1.3.0.tar.gz
	file in the top-level source code directory, you can run

	# installsardata

	This will attempt to unpack the Data file to the proper
	location.
```

---

### Post by unitedanarchy on 2012-06-05
Still

valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ ./configure Linux --prefix=/usr -v
./configure: 118: pconf/pconf: not found
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$

---

### Post by Kr0nZ on 2012-06-05
strange, does the 'pconf' folder exist in the 'searchandrescue_1.4.0' folder?
there should be a 'pconf' folder with a 'pconf' file inside of it.

Atleast from the source located [here]("http://linux.softpedia.com/progDownload/Search-And-Rescue-Download-19438.html"), which compiles on my system.

---

### Post by unitedanarchy on 2012-06-05
Yes indeed there is.

---

### Post by Kr0nZ on 2012-06-05
try
```
./configure --reset
```

then try again
```
./configure Linux --prefix=/usr -v
```

---

### Post by unitedanarchy on 2012-06-05
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ SearchAndRescue &
[1] 27449
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$ Search and Rescue was unable to find the data files in:

    /usr/share/games/searchandrescue
Please verify that you have installed the program properly. If you have installed the global data files in a non-standard location, then you should set the environment variable "SEARCHANDRESCUE_DATA" to refer to that non-standard location.
^C
[1]+  Exit 1                  SearchAndRescue
valeskagrim@ValeskaGrim:~/Desktop/**** to observe later/searchandrescue_1.4.0$

---

