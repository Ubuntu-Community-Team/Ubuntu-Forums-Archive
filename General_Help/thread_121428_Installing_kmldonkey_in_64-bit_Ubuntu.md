---
title: "Installing kmldonkey in 64-bit Ubuntu"
date: 2006-01-25
forum: General Help
---

### Post by Wolfbite on 2006-01-25
I'm going slightly mad from not getting it to work. I've installed the mldonkey core, and I'm now trying to install kmldonkey. In the readme it says:

To compile and install KMLDonkey, follow this procedure: 

 1. $ tar jxvf kmldonkey-0.10.1.tar.bz2
 2. $ cd kmldonkey-0.10.1
 3. $ ./configure --prefix=$(kde-config --prefix)
 4. $ make
 5. $ su -c "make install"

the three first isn't a problem, but when I try to "make", it says:

make: *** No targets specified and no makefile found.  Stop.

There are four makefiles in the directory as far as I can see, and I've also installed build-essential, so I don't see what could be wrong. Except for the last lines in part 3 when i run the configure thingy. After a million lines of data, where I get a lot of noes and yesses, it says:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Now what does that mean, I wonder, and could it be the problem? Help would be greatly appreciated. :)

PS: I've put the klmdonkey folder in home/Downloads, if that changes anything.

---

### Post by Wolfbite on 2006-01-25
Might as well bump this one too! ^^

---

### Post by lupine_nickt on 2006-01-25
Don't know. I use aMule (which is in repositories, so much less hassle :) ). 

Still. See if there is actually a makefile in the kmldonkey directory. That seems to be the problem :). If configure is failing, then the makefile won't be generated, IIRC.  (but don't quote me on that). Try "apt-get install libx11-dev" - that might fill in your deps problem.

xF,

...Nick

---

### Post by Wolfbite on 2006-01-25
[QUOTE=lupine_nickt]Don't know. I use aMule (which is in repositories, so much less hassle :) ). 

Still. See if there is actually a makefile in the kmldonkey directory. That seems to be the problem :). If configure is failing, then the makefile won't be generated, IIRC.  (but don't quote me on that). Try "apt-get install libx11-dev" - that might fill in your deps problem.

xF,

...Nick[/QUOTE]

Thanks for the reply, but it didn't get me any further. :(

---

