---
title: "making a deb the easy way"
date: 2009-10-29
forum: General Help
---

### Post by karimruan on 2009-10-29
Okay, I have a python file (.py) it is a small game I want to try to convert to a deb. I don't understand all of the tutorials I have found. Can anyone either point me to a noob friendly how to that walks you through EVERY step, or give me one yourself. I just don't understand any of it.
Thanks in advance!

---

### Post by Lars Noodén on 2009-10-30
It'd help if you mentioned which tutorials and howtos you have looked at already so we can see which ones were confusing.

How about this one?  It may be considered clear:
[http://users.telenet.be/mydotcom/howto/linux/package.htm](http://users.telenet.be/mydotcom/howto/linux/package.htm)

---

### Post by 3rdalbum on 2009-10-30
[http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/-wiki/CreatingDebianPackages](http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/-wiki/CreatingDebianPackages)

It talks a lot about what a package actually is.

Basically, you create a directory called "tmp". Inside "tmp" you put files and folders that you want to be in your package. So, if the package only provides two files, for instance /etc/myapp.conf and /usr/bin/myapp, then you'd create an /etc/ directory and put "myapp.conf" inside it; then you'd create a /usr directory, make a new /bin directory inside that, and then put the "myapp" file inside that.

Now inside the tmp folder, create a folder called DEBIAN and inside that, a file called "control". The contents of "control" should look something like this:

```
Package: blacklight3
Version: 0.2-1
Section: base
Priority: optional
Architecture: all
Suggests: ffmpeg, libavcodec-unstripped-51, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0
Maintainer: Christopher Lees <christopher_lees@anisp.com>
Description: Transfer videos to Sony Walkman MP3 players - CLI
 Blacklight3 allows you to transfer videos to Walkman MP3 players,
 in the very specific format that they require.
 It supports any ffmpeg-readable file as input.
 
 This program is the command-line backend.
```

Change any fields as you see fit.

Now run the following command in the directory above tmp:

```
dpkg-deb -b tmp blacklight3_0.2-1_all.deb
```

You need a specific naming scheme for your packages: The package name, then an underscore (_), then the package version, then another underscore, then the architecture (for a Python script, you can choose "all"). This must match what you have in the "control" file.

If there is anything about your package that you need to change, the dpkg-deb utility will tell you.

That's basically the short version of it.

---

### Post by karimruan on 2009-10-30
Okay, I am trying to package a .py file and a file called control.

I am getting the following error when running
 dpkg-deb -b dicerollerextreme_1.0_all:


[/code]

mat@karim-ruane:~$ dpkg-deb -b tmp dicerollerextreme_1.0_all.deb
dpkg-deb: failed to open package info file `tmp/DEBIAN/control' for reading: No such file or directory

[/code]

Here is my control file, just called 'control' (do I need a specific name and file type?):

```

Package: dicerollerextreme_1.0_all
Version: 1.0
Section: games
Priority: optional
Architecture: all
Essential: no
Depends: python_2.6
Installed-size: 1600
Maintainer: KarimRuan [karimruan@gmail.com]
Provides: dice_roller_extreme0.1a
Description: A dice rolling game where you lose lives for 
	     bad rolls, and gain points for high rolls. Very easy
             game.



```

THanks for the help!

---

### Post by karimruan on 2009-10-30
Okay, got it to build the DEB using dpkg-deb --build debian

I also got it to install. But not the way I want.

I would like to have it install into Applications>Games

But I guess I need to learn how. Don't even know where to begin a search for that. 

Again, help is appreciated!

EDIT: The game did not install to /usr/games/ but rather to / and the file is not executable. I marked it as executable, ran it in terminal (it is a text mode adaptation of another dice rolling game) but i get the following output:

Okay I can't get the output because the terminal keeps loading lives after I run the .py file and then quits out. What on earth did I do wrong?????

---

