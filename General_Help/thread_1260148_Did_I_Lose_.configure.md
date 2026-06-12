---
title: "Did I Lose ./configure???"
date: 2009-09-07
forum: General Help
---

### Post by ttoolin on 2009-09-07
Hi folks-

I continually find that I have a lot to learn, and this appears to be another learning opportunity . . .

. . . I was tinkering with installing software from source code, yesterday, and except for one attempt where the process was extremely well spelled-out, I really had no success.

I went back to it, today, and I think my ./configure script is missing.  I try to invoke it, try to get a help screen (using ./configure --help, ./configure -h, along with other variations of the same general process), and all I get is
[HTML]bash: ./configure: No such file or directory[/HTML]
Over and over again, I figured that I was just doing something wrong, but now I think it is gone (perhaps deleted, perhaps corrupted?).  I did a file search for 'configure' and got a number of hits, but nothing that looked like what I was looking for.  For all I know, it may be a command imbedded within another process.

It was functional, at least for one time, yesterday.  Do I need to reinstall or reload something???

Thanks.

---

### Post by blueridgedog on 2009-09-07
> **ttoolin said:**
> 
It was functional, at least for one time, yesterday.  Do I need to reinstall or reload something???


If you already installed it, then why are you wanting to re-run the configuration process?  If the install didn't work as expected, you can delete the directory you expanded the compressed source into and re-extract it, then reconfigure, make and make install.  The install process produced a binary file that you can use tho run the program.

For example, if I downloaded "Cool App" version 2.1, it may come as a file CoolApp2.1.tgz, upon extracting the files it would make a directory named CoolApp2.1 and inside that directory would be the source code and often a configuration script.  I could go into the directory and use the files or if things did not work I could go to the parent directory and rm -rf ./CoolApp2.1 .  At that point I would still have the original source and could re-extract the files from CoolApp2.1.tgz.

Can you share what you were trying to install?

---

### Post by 3rdalbum on 2009-09-07
Some source code is so simple to compile that it doesn't need any configuration; you can just make and sudo make install. Some source code requires a different build system like "scons" or "jam" and doesn't have a traditional configure script either.

---

### Post by ttoolin on 2009-09-07
I was trying a variety of programs, yesterday, that I downloaded from sourceforge.net.  There isn't really anything I need, I was just trying to get comfortable with the process of compiling and installing software that was not pre-packaged for ubuntu.  I no longer have the successful program, and I tried several.  Mostly games.  I pretty much tossed them as I went along

The one I am working with, today, is gemz-0.97.0.tgz, which I've uncompressed into another folder on my desktop.  It was working with that when it seemed as if ./configure just didn't exist, anymore, and it probably started seeming like it didn't exist sometime during my hours of tinkering, yesterday.

Although I'm more after learning the compiling and installation process, the game noted, above, is one I'd keep.  I would also keep a 3D Scrabble that I never had success with, yesterday, and have since deleted.  There is also one other file for which there is a new version available, but synaptic doesn't have it (BOINC).  The last time I tried (maybe a month ago), it installed all over my desktop.  I think I've now learned enough to specify the target directory for it.  From what I gather, that is a function of ./configure, but I'm having little luck with that, at the moment :(

It may seem strange that there really isn't a program I'm after, I'm just trying to be comfortable that I could install one, if I wished to do so.

Thanks.

---

### Post by oldos2er on 2009-09-07
BOINC doesn't need to be compiled; just download and run the .sh file.

[http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

---

### Post by ttoolin on 2009-09-07
Thanks! for the advice on BOINC.

terry

---

