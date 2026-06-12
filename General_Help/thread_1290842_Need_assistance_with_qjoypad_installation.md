---
title: "Need assistance with qjoypad installation"
date: 2009-10-14
forum: General Help
---

### Post by jukingeo on 2009-10-14
Hello all,

You know...one of my big complaints with Linux (and I don't have many complaints), is that documentation for installation should be straightforward.   Normally this is the case with Add/Remove programs or using a repository through Synaptic.  With these convenient ways of installing a program WHY are program creators still having Linux users use the older archaic tar.gz "make, make install" method.   Most of the time this creates confusion and delay.  This instance is no different.

Following the instructions to the letter for installing qjoypad on my system this is what I am reading directly from the install text file that comes with the program:

For a quick install, just follow these steps:

tar -xzvf qjoypad-3.?.tgz
cd qjoypad-3.?/src
./config
make
make install

If those steps don't work for you, give the README a look!


Ok, that sounds simple enough, but when I go into the terminal and try to install the program, this is what I am getting:

geo@home:~/qjoypad-4.0.0/src$ ./config
_./config: line 66: qmake: command not found_

Configuring QJoyPad installation...
------------------------------------------------------------

Device directory: /dev/input
-- Devices will be looked for in:
     /dev/input/js0
     /dev/input/js1
     etc.

Prefix directory: /usr/local
-- Files to be installed in:
     /usr/local/bin
     /usr/local/doc
     /usr/local/share/pixmaps
	 
---------------------------------------------------------
If these settings are okay, go ahead and run 'make' and
then 'make install'.

To make changes, run ./config --help for details.

geo@home:~/qjoypad-4.0.0/src$ make
make: *** No targets specified and no makefile found.  Stop.
geo@home:~/qjoypad-4.0.0/src$ 


So apparently something is amiss, and I am guessing it has to do with the part I underlined above.

Normally I avoid tar.gz file programs because of hassles like this and just stick with the Synaptic repository (or self installing files) but I would really like to use this program because I need it to assign key presses to a joystick.

Also, while we are on the topic...is there an installer for tar.gz files that can be put on my system?

Thanx,

Geo

---

### Post by ArielEnter on 2010-11-20
install qt3-dev-tools if you are trying to compile qjoyapads 3.4.1 worked for me. I hear is a lot easier to compile 3.4.1 that the newest vertion number 4. Watch this post: [http://ubuntuforums.org/showthread.php?t=1147506&highlight=QJoyPad](http://ubuntuforums.org/showthread.php?t=1147506&highlight=QJoyPad)

---

