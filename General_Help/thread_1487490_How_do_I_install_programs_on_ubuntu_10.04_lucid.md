---
title: "How do I install programs on ubuntu 10.04 lucid"
date: 2010-05-19
forum: General Help
---

### Post by pr0t3g3 on 2010-05-19
I don't know how to install programs from the net on here >.< this is driving me up the wall.  Just about any program I download doesnt have an install option.... the hell?

---

### Post by aysiu on 2010-05-19
> **pr0t3g3 said:**
> I don't know how to install programs from the net on here >.< this is driving me up the wall.  Just about any program I download doesnt have an install option.... the hell?
Applications > Ubuntu Software Center

More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by amite on 2010-05-19
if u have downloaded any s/w with .deb extension u can install it from command line:
$ sudo dpkg -i package_name
also u can install them by double click on them.

and if u r trying to install .exe file then first install wine 
$sudo apt-get install wine
and then install .exe program with wine..

---

### Post by pr0t3g3 on 2010-05-19
the terminal wont let me install alien... instead of popping up a window like it shows in the article it asks for it inside the terminal ...ok... BUT IT WONT LET ME TYPE IT

---

### Post by pr0t3g3 on 2010-05-19
> **amite said:**
> if u have downloaded any s/w with .deb extension u can install it from command line:
$ sudo dpkg -i package_name
also u can install them by double click on them.

and if u r trying to install .exe file then first install wine 
$sudo apt-get install wine
and then install .exe program with wine..
thank you for your support ...


no offense :) but if I hear someone tell me to install wine one more time and let me die in the dark with it I'm going to lose it!


wait a minute I never uninstalled it ... grrr....

---

### Post by aysiu on 2010-05-19
What are you trying to install that you need *alien*?

---

### Post by elliotn on 2010-05-19
```
sudo apt-get install vlc
```
u can change the vlc to audacity etc just put the name of the program

---

### Post by amite on 2010-05-19
can u please elaborate what is happening ...........

r u permit to use sudo(r u sudoer)?

---

### Post by pr0t3g3 on 2010-05-19
> **elliotn said:**
> ```
sudo apt-get install vlc
```u can change the vlc to audacity etc just put the name of the program
[-o< thank you!!!  


sheesh.. if only my other posts had this kind of help T_T no really I seriously did die in the dark with wine and thats not the worst part.. I was beaten with a stick by hikaricore... b-word had an invisible light >.> ....

---

### Post by elliotn on 2010-05-19
> **pr0t3g3 said:**
> [-o< thank you!!!  


sheesh.. if only my other posts had this kind of help T_T no really I seriously did die in the dark with wine and thats not the worst part.. I was beaten with a stick by hikaricore... b-word had an invisible light >.> ....

you can also use the SOFTWARE CENTER if u dont like commands

---

### Post by pr0t3g3 on 2010-05-19
its still not letting me type my password for confirmation

---

### Post by pr0t3g3 on 2010-05-19
> **elliotn said:**
> you can also use the SOFTWARE CENTER if u dont like commands there are a few programs I want to install python is one of them ... but a few others well... the thing is it wont let me type my password in the terminal;  when I press a few keys they just don't register... I don't think it's computer >.< it's usually me anyways.. so help? bah .... I checked the thing as resolved.. whats wrong with me...

---

### Post by elliotn on 2010-05-19
the password wont appear just type it and enter

---

### Post by ankit singh on 2010-05-19
hey look at this
[http://www.raymond.cc/blog/archives/2010/05/19/installing-via-terminal-and-compiling-files-from-source/](http://www.raymond.cc/blog/archives/2010/05/19/installing-via-terminal-and-compiling-files-from-source/)

---

### Post by pr0t3g3 on 2010-05-19
> **elliotn said:**
> the password wont appear just type it and enter


yeah I tried that -_- didn't work .. just typed my pass in and hit enter it did nothing..

---

### Post by elliotn on 2010-05-19
k just try 

sudo su

and see if ur password will work btw what does it say when u press enter after the password

---

### Post by ankit singh on 2010-05-19
post what is happening in ur terminal.

---

### Post by pr0t3g3 on 2010-05-19
it's actually not saying anything after I type it .. it's just closing out... I thought it was because I accidentally hit my touch pad and it closed it out... it seems that's not the case... 
I type my pass .. hit enter... boom.... gone...

---

### Post by ankit singh on 2010-05-19
close all terminal and open new one and run some application using sudo command
eg sudo firefox and say what happened.

---

### Post by elliotn on 2010-05-19
he must also try to restart x

---

### Post by ryan858 on 2010-05-19
For future reference; if you ever need a program that you can't get in the Ubuntu repositories, or in .deb format... it'll likely be in *.tar.gz* format, which is a *"tarball"*, a compressed (or 'zipped' for lack of a better word) *source code* for the program. Most of these can be extracted using either a file manager or terminal. In file manager you just right click and click **extract here**. Command line is:
**$ tar xvzf <filename>**
for gzip archives (tar.gz) or
**$ tar xvjf <filename>**
for bzip2 archives (.tar.bz2)

**x** for e**x**tract
**v** for **v**erbose
**z** for g**z**ip
**j** for bzip2 (I know, I know!)
**f** for **f**ile (to tell it you wanna output to file, not something else)

For more info:[B]
$ tar --help[/B]


Anyways, with source code, you have to compile it yourself... This is usually as simple as:
[B]$ cd [I]<directory of extracted source code>
[/I]$ ./configure
$ make
$ make install
[/B]
or how I like to do it:
**$cd *<directory>* && ./configure && make && make install**
(exucutes all of the commands in one line, but if one of the commands returns an error, then the rest after it will not be executed)

For other types of source, you'll have to look it up yourself.

---

### Post by pr0t3g3 on 2010-05-19
> **ryan858 said:**
> For future reference; if you ever need a program that you can't get in the Ubuntu repositories, or in .deb format... it'll likely be in *.tar.gz* format, which is a *"tarball"*, a compressed (or 'zipped' for lack of a better word) *source code* for the program. Most of these can be extracted using either a file manager or terminal. In file manager you just right click and click **extract here**. Command line is:
**$ tar xvzf <filename>**
for gzip archives (tar.gz) or
**$ tar xvjf <filename>**
for bzip2 archives (.tar.bz2)

**x** for e**x**tract
**v** for **v**erbose
**z** for g**z**ip
**j** for bzip2 (I know, I know!)
**f** for **f**ile (to tell it you wanna output to file, not something else)

For more info:[B]
$ tar --help[/B]


Anyways, with source code, you have to compile it yourself... This is usually as simple as:
[B]$ cd [I]<directory of extracted source code>
[/I]$ ./configure
$ make
$ make install
[/B]
or how I like to do it:
**$cd *<directory>* && ./configure && make && make install**
(exucutes all of the commands in one line, but if one of the commands returns an error, then the rest after it will not be executed)

For other types of source, you'll have to look it up yourself.
Thanks Its done I got it; and thanks for the tips!

---

