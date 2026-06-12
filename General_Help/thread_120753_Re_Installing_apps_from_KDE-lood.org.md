---
title: "Re: Installing apps from KDE-lood.org"
date: 2006-01-23
forum: General Help
---

### Post by throntax on 2006-01-23
tgz means it's a zip file, like .zip...
you have to uncompress it first!

type 
tar xzvf crystal-0.9.8-i686-1pfabregat.tgz
from the directory the file is in and it should uncompress into it's own directory

It's compressed twice; the tgz extension is the same as one you might see= .tar.gz
you could uncompress it twice if you wanted; 
gunzip <filename.tar.gz>
then 
tar xvf <filename.tar>
but we just use the 'z' with tar, its much easier :)

edit: is this post at the right end of the thread? somehow it is at the top, not the end...

---

### Post by shafer5 on 2006-01-23
[QUOTE=throntax]tgz means it's a zip file, like .zip...
you have to uncompress it first!

type 
tar xzvf crystal-0.9.8-i686-1pfabregat.tgz
from the directory the file is in and it should uncompress into it's own directory

It's compressed twice; the tgz extension is the same as one you might see= .tar.gz
you could uncompress it twice if you wanted; 
gunzip <filename.tar.gz>
then 
tar xvf <filename.tar>
but we just use the 'z' with tar, its much easier :)

edit: is this post at the right end of the thread? somehow it is at the top, not the end...[/QUOTE]

its definently at the top

---

### Post by shafer5 on 2006-01-23
ok..please tell me which one i am suppose to DL

here's the site:
[http://kde-look.org/content/show.php?content=13969](http://kde-look.org/content/show.php?content=13969)

---

### Post by shafer5 on 2006-01-23
I was wondering how I can install apps from KDE-look.org? I have DL'd the crystal window decoration but have no idea how to install anything? 

Thanks

---

### Post by skaboss on 2006-01-23
In order to use these win decorations, you will have to compile them : 
```

$ cd path/to/whereyouunzippedthefiles
$ ./configure --prefix=`kde-config --prefix`
$ make
# make install  (as root)

```

The configure and make commands will probably show you some errors, due to missing libs. To avoid that, first install (via adept or synaptic) : [LIST]
[*]kdebase-dev
[*]kdelibs4-dev
[/LIST]

Have fun !

---

### Post by shafer5 on 2006-01-23
ok i installed the packages :    kdebase-dev
                                                kdelibs4-dev

i have a window dec. tgz file downloaded in my home folder

> anderson@kubuntu:~$ cd home/anderson/crystal-0.9.8-i686-1pfabregat.tgz
bash: cd: home/anderson/crystal-0.9.8-i686-1pfabregat.tgz: No such file or directory

i dont understand

---

### Post by goombah88 on 2006-01-24
[QUOTE=shafer5]ok i installed the packages :    kdebase-dev
                                                kdelibs4-dev

i have a window dec. tgz file downloaded in my home folder



i dont understand[/QUOTE]

A *.tgz file is just that, a file.  You can't "cd" into a file, only into folders.  go into the folder the .tgz file is in and extract it from there.  then "cd" into the folder it created and take it from there.  hope this helps.

---

### Post by shafer5 on 2006-01-24
[QUOTE=goombah88]A *.tgz file is just that, a file.  You can't "cd" into a file, only into folders.  go into the folder the .tgz file is in and extract it from there.  then "cd" into the folder it created and take it from there.  hope this helps.[/QUOTE]

when you extract it, it has 2 folders- opt folder and install folder....which one do i go to

---

### Post by shafer5 on 2006-01-24
That is what i got....are you able to install these apps with ubuntu kde? or is it strickly for kubuntu?

> anderson@ubuntu:~/opt$ cd /home/anderson/install
anderson@ubuntu:~/install$ ./configure --prefix=`kde-config --prefix`
bash: ./configure: No such file or directory

---

### Post by GeneralZod on 2006-01-24
You should download the [source](http://kde-look.org/content/download.php?content=13969&id=1&PHPSESSID=2cb1da0d789b76c54083120440941f3c) download, not the Slackware one :)

Here's a screenie I just took:

[http://etotheipiplusone.com/crystal-kde-screenshot.png](http://etotheipiplusone.com/crystal-kde-screenshot.png)

Edit:

If you're feeling adventurous later on, and have working 3D acceleration, you might want to check out [CrystalGL](http://www.kde-look.org/content/show.php?content=18983).

---

### Post by GeneralZod on 2006-01-24
To answer your PM:

To get a working compiler, do

```

sudo apt-get install build-essential

```

---

### Post by shafer5 on 2006-01-24
[QUOTE=GeneralZod]To answer your PM:

To get a working compiler, do

```

sudo apt-get install build-essential

```[/QUOTE]

ok here is what i have up to this point

```

$ cd path/to/whereyouunzippedthefiles
$ ./configure --prefix=`kde-config --prefix`
$ make

```

how do i do the (in other words how do i become the root to do that? If that is the right thing to do?) What i did was type cd /root? :
#make install

---

### Post by GeneralZod on 2006-01-24
So the "./configure" finished OK? Did "make" return any errors?

If both "./configure" and "make" completed successfully, then we just need to install crystal which, as you noted, requires root privileges which we obtain using "sudo".  It's wise to use "checkinstall" rather than the more traditional "make install" as it gives you an easy way to remove it if you don't like it.

So go back to the directory where you performed the "./configure" and "make", and so

```

sudo checkinstall -D

```

You'll be asked for a description of the package; enter pretty much whatever you want (I entered "crystal KDE window decoration"), accept the defaults whenever you're asked, and that should be it, hopefully.

---

### Post by shafer5 on 2006-01-24
ok...getting error now

```
anderson@ubuntu:~/crystal-0.9.8$ sudo check install -D
sudo: check: command not found

```

---

### Post by GeneralZod on 2006-01-24
"checkinstall" is all one word :)

I forgot to mention - I don't think that checkinstall is installed by default, so do

```

sudo apt-get install checkinstall

```

first.

Good luck!

---

### Post by shafer5 on 2006-01-24
```
*** Warning: The package name "crystal-0.9.8" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values:

0 -  Maintainer: [ root@localhost.localdomain ]
1 -  Summary: [ crystal KDE window decoration ]
2 -  Name:    [ crystal-0.9.8 ]
3 -  Version: [ 0.9.8 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ crystal-0.9.8 ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue:  

```

what do i do here?




EDIT*** wow.....n/m that...somehow i missed the big press ENTER

---

### Post by GeneralZod on 2006-01-24
Working yet? :)

---

### Post by shafer5 on 2006-01-24
lol.......no

i am such a n00b at this stuff...dont laugh:)

but...

where do i find it? you do know i have ubuntu right? everything is installed and says its there so....

**edit**  i did install the KDE enviorment tho

---

### Post by GeneralZod on 2006-01-24
[QUOTE=shafer5]lol.......no

i am such a n00b at this stuff...dont laugh:)

but...

where do i find it? you do know i have ubuntu right? everything is installed and says its there so....[/QUOTE]

Oh, right - it's not an application, *per se*, so you won't find it in any of the menus.

If you go to K-Menu->System Settings-> Appearance-> Window Decorations, you'll find it in the drop-down list.  See the screenshot I posted on the previous page :)

---

