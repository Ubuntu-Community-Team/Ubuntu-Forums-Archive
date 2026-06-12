---
title: "tar download"
date: 2011-10-04
forum: General Help
---

### Post by tobythedog on 2011-10-04
hi i want to install stuffkeeper, have dowload tar file , what am i supposed to do with it now to install it , tried clicking on it and opening , this opens arcive manager. just cannot work out what i shoul do next,help please.

---

### Post by haqking on 2011-10-04
> **tobythedog said:**
> hi i want to install stuffkeeper, have dowload tar file , what am i supposed to do with it now to install it , tried clicking on it and opening , this opens arcive manager. just cannot work out what i shoul do next,help please.

HI and welcome to forums

**First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set ;-)

Have fun

Regards

haqking

---

### Post by tobythedog on 2011-10-04
still no clearer ,i keep looking at different things, all so complicated it seems unbelievable that someone like me should spend 6 months learning how to install a program , and may never work it out . its very annoying as it took me months to find the stuffkeeper program i cannot find anything else that could do what i want.why is it so hard to do something that would take seconds on windows, dont get me wrong i am no fan of windows, but why is it so hard to install some programs on ubuntu.

---

### Post by haqking on 2011-10-04
> **tobythedog said:**
> still no clearer ,i keep looking at different things, all so complicated it seems unbelievable that someone like me should spend 6 months learning how to install a program , and may never work it out . its very annoying as it took me months to find the stuffkeeper program i cannot find anything else that could do what i want.why is it so hard to do something that would take seconds on windows, dont get me wrong i am no fan of windows, but why is it so hard to install some programs on ubuntu.

because you have control in Linux, you dont have any control in windows.

let me take a look at the stuffkeeper thing, i will be back

---

### Post by haqking on 2011-10-04
Well 2 seconds and i found this [http://www.stuffkeeper.org/index.php?title=Installation](http://www.stuffkeeper.org/index.php?title=Installation)

and also it has a PPA [https://launchpad.net/~qball-qballcow/+archive/ppa](https://launchpad.net/~qball-qballcow/+archive/ppa) which you could add, though it is out of date, it looks like the program stopped devlopment a few years ago

---

### Post by tobythedog on 2011-10-04
thanks for the help. i have tried to follow the instalatin on the stuffkeeper web page i have done the first bit as below.
You can compile stuffkeeper either from a release, or bleeding edge from git. 
git

For this you need git installed. 
git clone git://repo.or.cz/stuffkeeper.git

This will create a copy of the development tree inside 'stuffkeeper/' 

To compile a copy from git you need as extra dependency gob2.

i however dont understand what the gob2 bit is and what if anything i need to do

---

### Post by haqking on 2011-10-04
> **tobythedog said:**
> thanks for the help. i have tried to follow the instalatin on the stuffkeeper web page i have done the first bit as below.
You can compile stuffkeeper either from a release, or bleeding edge from git. 
git

For this you need git installed. 
git clone git://repo.or.cz/stuffkeeper.git

This will create a copy of the development tree inside 'stuffkeeper/' 

To compile a copy from git you need as extra dependency gob2.

i however dont understand what the gob2 bit is and what if anything i need to do

why do you need the bleeding edge ? use a stable release and follow instructions below that part.

if you need gob

```
sudo apt-get install gob2
```

---

### Post by tobythedog on 2011-10-04
because i have no idea what i am doing , i dont know how to install this program , that is my problem and despite spending several days and many hours i still cannot work out how to install it . i have tried the release , when i enter this inti the terminal i get 
tar (child): stuffkeeper-0.08.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

i have also trie downloading a tar file from somwhere else of stuffkeeper, which i think i have managed ok but now i am stuck again as i dont understand what to do with it ther is a readme file with it but i cannot understand any of it

---

### Post by haqking on 2011-10-04
> **tobythedog said:**
> because i have no idea what i am doing , i dont know how to install this program , that is my problem and despite spending several days and many hours i still cannot work out how to install it . i have tried the release , when i enter this inti the terminal i get 
tar (child): stuffkeeper-0.08.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

i have also trie downloading a tar file from somwhere else of stuffkeeper, which i think i have managed ok but now i am stuck again as i dont understand what to do with it ther is a readme file with it but i cannot understand any of it

the instructions are there step by step and in the links i originally posted.

```
tar -jxf stuffkeeper-0.08.tar.bz2
```

if that is the name of the .tar you downloaded and make sure you are in the directory of where that file is which is probably Downloads, but like i said in my first post you can right click on it and choose extract.

go to terminal and then follow the instructions step by step as they are laid out for you.

---

### Post by tobythedog on 2011-10-04
maybe i just got a bit further i think i have managed to extract the files but again i am no wiser on what to do next , there is an install file which when i click it sats see readme , the readme file is below
Requirments:
============
The following libraries and programs are required to compile stuffkeeper:
make
gcc
automake        >= 1.6
autoheader
aclocal
autoconf	>= 2.59
intltool        >= 0.21 
libtoool
glib-2.0        >= 2.16
gtk+-2.0        >= 2.12
gmodule-2.0
libglade-2.0
sqlite3
gio-2.0
ghtread-2.0
gob2            >= 2.0.10

Compile options:
================
The following options are available, they are available for debuggin purpose only.
--enable-debug  Outputs extra debug information.
--enable-timing Outputs timing information.

Compiling:
==========
Release
-------
./configure <compile options>
make
make install

Git
---
./autogen.sh <compile options>
make
make install


can you tell me what i need to do next, maybe i am thick or something but i just cannot work it out

---

### Post by haqking on 2011-10-04
> **tobythedog said:**
> maybe i just got a bit further i think i have managed to extract the files but again i am no wiser on what to do next , there is an install file which when i click it sats see readme , the readme file is below
Requirments:
============
The following libraries and programs are required to compile stuffkeeper:
make
gcc
automake        >= 1.6
autoheader
aclocal
autoconf	>= 2.59
intltool        >= 0.21 
libtoool
glib-2.0        >= 2.16
gtk+-2.0        >= 2.12
gmodule-2.0
libglade-2.0
sqlite3
gio-2.0
ghtread-2.0
gob2            >= 2.0.10

Compile options:
================
The following options are available, they are available for debuggin purpose only.
--enable-debug  Outputs extra debug information.
--enable-timing Outputs timing information.

Compiling:
==========
Release
-------
./configure <compile options>
make
make install

Git
---
./autogen.sh <compile options>
make
make install


can you tell me what i need to do next, maybe i am thick or something but i just cannot work it out

no offence but can you read the link ive posted and follow the instructions, download the file, extract it which it sounds like you have done.

So now follow the instructions here [http://www.stuffkeeper.org/index.php?title=Installation](http://www.stuffkeeper.org/index.php?title=Installation) from the part where it says for Ubuntu users.

after the first command the others need to be carried out in the directory of the extracted files, post back when and where you have problems if any

---

### Post by tobythedog on 2011-10-06
thanks again for the help, afraid i am totaly stuck again i cannot work out what to do next i have been to the stuffkeepeer page and tried everything i can possibly think of and i get nowhere at all. i have tried the ubunturepository link and this wont work as when following the instructions terminal comes back with it cannot locate stuffkeeper package. if i trie the first page and tri getting the release i get the folowing.
tar (child): stuffkeeper-0.08.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

i am sorry to be suck a pain but i just do not understand what to do next

---

### Post by tobythedog on 2011-10-06
i also do not understand what i need to do about all this
The following libraries and programs are required to compile stuffkeeper:
 make
 gcc
 automake >= 1.6
 autoheader
 aclocal
 autoconf >= 2.59
 intltool >= 0.21 
 libtoool
 glib-2.0 >= 2.16
 gtk+-2.0 >= 2.12
 gmodule-2.0
 libglade-2.0
 sqlite3
 gio-2.0
 ghtread-2.0
 gob2 >= 2.0.10 

do i need to install all of these before i can get stuffkeeper and if so how do i do that please.

---

### Post by haqking on 2011-10-06
> **tobythedog said:**
> i also do not understand what i need to do about all this
The following libraries and programs are required to compile stuffkeeper:
 make
 gcc
 automake >= 1.6
 autoheader
 aclocal
 autoconf >= 2.59
 intltool >= 0.21 
 libtoool
 glib-2.0 >= 2.16
 gtk+-2.0 >= 2.12
 gmodule-2.0
 libglade-2.0
 sqlite3
 gio-2.0
 ghtread-2.0
 gob2 >= 2.0.10 

do i need to install all of these before i can get stuffkeeper and if so how do i do that please.

ok so from the page, have you downloaded a release, if so where is it and what is it called:

example would be

tar -jxf stuffkeeper-0.08.tar.bz2

and it is in your /home/yourusername/Downloads probably ?

if so then next step on the page provided is type the following into terminal:


```
sudo apt-get install build-essential libgtk2.0-dev libglib2.0-dev libglade2-dev libsqlite3-dev intltool libgtkspell-dev gob2 git 
```

doing this installs the list you asked about, so for some reason you are not following the instructions on the link

so did you do that if so any errors ?

are you at this stage ? not done it ? if not then why not ?

---

### Post by tobythedog on 2011-10-06
yes and no , i cannot get the following instruction to work tar -jxf stuffkeeper-0.08.tar.bz2 when i try this i get this  tar (child): stuffkeeper-0.08.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


so i tried to find a dowload somewhere else which i think i have done and have extracted it i think . it is in my downloads files and is called stuffkeeper-0.12.0 
 i dont know what to do with it and this is where i am stuck

---

### Post by haqking on 2011-10-06
> **tobythedog said:**
> yes and no , i cannot get the following instruction to work tar -jxf stuffkeeper-0.08.tar.bz2 when i try this i get this  tar (child): stuffkeeper-0.08.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


so i tried to find a dowload somewhere else which i think i have done and have extracted it i think . it is in my downloads files and is called stuffkeeper-0.12.0 
 i dont know what to do with it and this is where i am stuck

are you in the directory where this file is located ?

is the name of the file the same as above ie  stuffkeeper-0.08.tar.bz2  ?]

and like i said before, once you have downloaded the file you can right click on it to extract it then just carry on with the instructions about installing the dependencies for compiling

---

### Post by tobythedog on 2011-10-06
how do i get in the directory of the file

---

### Post by haqking on 2011-10-06
> **tobythedog said:**
> how do i get in the directory of the file

in terminal use the cd command

so

cd pathname/pathname/

example would be

cd /Downloads

if Downloads is in your home directory which is the default working directory from your prompt

or use your file manager to tell me where it is and i will show you what to type.

also what is the name of the file you downloaded, and why not just right click it to extract it instead of attempting the above command

---

### Post by tobythedog on 2011-10-06
how do i use the file manager to tell me where it is ,i have opened it and looked  everywhere i can find but find nothing that tells me where it is

---

### Post by haqking on 2011-10-06
> **tobythedog said:**
> how do i use the file manager to tell me where it is ,i have opened it and looked  everywhere i can find but find nothing that tells me where it is

well where did you save it to when you downloaded it.

is it not in your Downloads folder which is in your home directory ?

---

### Post by tobythedog on 2011-10-06
yes it appears to be in the download folder as stuffkeeper-0.12.0

---

### Post by haqking on 2011-10-06
> **tobythedog said:**
> yes it appears to be in the download folder as stuffkeeper-0.12.0

ok so right click on it and choose extract and it should create a new folder in the Downloads folder with the same name

post back when you have done this

---

### Post by tobythedog on 2011-10-06
well i right click and no extract option , it opens the file and there are several files here , i think that this is the extracted file maybe as i extracted it before

---

### Post by haqking on 2011-10-06
> **tobythedog said:**
> well i right click and no extract option , it opens the file and there are several files here , i think that this is the extracted file maybe as i extracted it before

well an extracted file would be a folder containing files, so is it a file or a folder.

anyways i suspect it is a file which we now know is in Downloads

so in terminal type

```
cd Downloads
```

then type

```
tar -jxf <filename>
```

where the <filename> is the exact filename of the file, if you unsure then post the contents of

```
ls
```

back here so i can tell you what to type

---

### Post by haqking on 2011-10-06
on that note however i am off to bed.

you need to change to the downloads location to run the tar extraction command.

then follow the instruction on the website to install dependencies.

or i can cut and paste them back here for you.....LOL

---

