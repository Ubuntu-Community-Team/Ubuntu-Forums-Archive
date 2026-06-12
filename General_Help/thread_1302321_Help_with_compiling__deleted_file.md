---
title: "Help with compiling / deleted file"
date: 2009-10-26
forum: General Help
---

### Post by snowguy on 2009-10-26
Hi all--need help, please. For my daughter who is 10 who lost a lot of school work!

My daughter was using ubuntu with openoffice word processor for a school assignment. She had literally been working on this project for days and spent countless hours on it. It is a mystery about Christopher Columbus that she was supposed to write for her class. Anyway, somehow the file had been saved in the TMP directory. I don't know how that happened. She'd been doing it with my wife and neither are very computer literate so they didn't notice. (It may be because my daughter had e-mailed a draft to someone at the end of last week and, I'm guessing, she opened it right from the draft. I don't know.) I'm also not sure how it is that she had been using it for days without losing it earlier. Maybe she had left the computer on or somehow it didn't happen to delete the TMP directory earlier. BUT, today the assignment was due. She went to print it off to turn it in and POOF--it was gone. I can't believe that it happened only right when it was due. 

Sooo....I said I'd try to recover it but so far I've had no luck. 

Here's what I've done so far ...

After reading [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) it seemed that foremost was the best option. Unfortunately, it turns out when I read more about it that foremost doesn't support odf files :(. So after searching around I decided on going with extundelete [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/) .

Luckily I already had a separate partition with a separate installation of ubuntu on it so I could work on the computer without messing up further that partition.  

Unfortunately, this is my first experience trying to compile something in ubuntu and I don't have any clue what I'm doing.  Here's what I've done:

Per [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) I installed:

sudo apt-get install build-essential
sudo apt-get install checkinstall

Per the readme file that came with extundelete I installed:

sudo apt-get install e2fslibs-dev

Then I went to the src subdirectory of extundelete-0.1.8 and ran (following the community instructions for compiling  I linked to above):

sudo checkinstall

That didn't work. So instead I followed the directions in the readme and tried 

sudo make

That printed off a bunch of stuff that to me suggested it works but when I tried extundelete --help I got the error  "bash: extundelete: command not found." So I figured it didn't work. 

Any suggestions???

I'm desperate for help. Any help is much appreciated...

---

### Post by nothingspecial on 2009-10-27
After make type sudo checkinstall.

You have to do them both.

---

### Post by snowguy on 2009-10-28
Tried doing both as you suggest but I get this when I run makeinstall.

```

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
...
========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

btw, here is what I get when I run Make.
```
xxx@xxx:~/Desktop/extundelete-0.1.8/src$ sudo make

g++ -I. -g -W -Wall -Wredundant-decls -Wshadow -Woverloaded-virtual -Wpointer-arith -Wwrite-strings -c -o extundelete.o `test -f 'extundelete.cc' || echo './'`extundelete.cc
g++ -I. -g -W -Wall -Wredundant-decls -Wshadow -Woverloaded-virtual -Wpointer-arith -Wwrite-strings -c -o block.o `test -f 'block.c' || echo './'`block.c
g++ -I. -g -W -Wall -Wredundant-decls -Wshadow -Woverloaded-virtual -Wpointer-arith -Wwrite-strings -c -o insertionops.o `test -f 'insertionops.cc' || echo './'`insertionops.cc
g++ -o extundelete  extundelete.o block.o insertionops.o -lext2fs

xxx@xxx:~/Desktop/extundelete-0.1.8/src$ 

```

Help, Anyone?

---

### Post by fluffman86 on 2009-10-28
try photorec:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

No need to compile.  Just download and extract the "linux" version to your desktop.  Open a terminal and run:
sudo ~/Desktop/testdisk-6.11.3/linux/photorec_static

---

### Post by snowguy on 2009-10-31
Thanks for the suggestion. I didn't try photorec. I did figure out how to make foremost work. The trick was something I came across somewhere which says for openoffice files look for zip files. And in fact using foremost I was able to find several openoffice documents, in fact way too many and a bunch of other zip files that had been erased from the drive and the problem was that I don't think the proper file was restored BUT i'm not sure because literally thousands of files were restored and short of open up each zip file and renaming it as .odt and then looking at the doc I couldn't figure out what the right document was. ughh...

So I didn't try photorec because looking at the description it seems like I'd have the same problem. So I returned to some other things. (This is really for the benefit of others who end up having a similar problem) and here's what happened. 

I was able to install ext3grep from synaptic but it has some bug in it wherein everytime I ran it it would fail in the second state with an error: 

ERROR: dir_inode_to_block(11193) returned -1.

and it would just stop after that.
So I was adventurous and tried uninstalling ext3grep using synaptic file and then getting the source code and compiling it--hoping that maybe I could (and this is a real strech for me) just make some tweak to convince it to skip 11193. BUT unfortuantely I still cannot figure out how to compile. Same problem now. It seems to work but nothing actually happens, i.e. I get the error: 

sudo: ext3grep: command not found

So I'm determined to try to get this using either ext3grep or extundelete (because each of these in theory allow me to specify the file I want to undelete vs digging up every past file ever on the computer and making me sesarch them). 

I think I'm going to post asking for help compiling in the dev list but if anyone has a suggestion for me here I would really appreciate it. Not sure what I'm doing wrong to compile these two modules (ext3grep and extundelete)

---

