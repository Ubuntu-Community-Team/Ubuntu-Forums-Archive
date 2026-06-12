---
title: "trying to get pbasic compiler on linux"
date: 2009-07-03
forum: General Help
---

### Post by devin0 on 2009-07-03
I have been trying to move my microcontroller programming from windows to linux. I use the basic stamp microcontroller. I have sucessfully  installed the basic stamp tokenizer library [http://bstamp.sourceforge.net/](http://bstamp.sourceforge.net/) and am now trying to get the pbasic editor running. The pbasic editor is offered from the parallex website [http://www.parallax.com/tabid/441/Default.aspx](http://www.parallax.com/tabid/441/Default.aspx)
I have follwed the instructions in the editors included readme file and copied the lib files to where they belong, but when I go to run the editor the program splash screen pops up and nothing else happens. What can I do to fix this?

---

### Post by michy99 on 2009-07-03
What error messages do you get if you start the program from a terminal?

---

### Post by michy99 on 2009-07-03
You might find this helpful. It is written for KDE instead of Gnome, but you might be able to adapt it.

[http://www.gaess.ch/?page_id=5](http://www.gaess.ch/?page_id=5)

EDIT: I found an IDE for Gnome that might be worth a look:

[http://www.robbayer.com/roboide.php](http://www.robbayer.com/roboide.php)

---

### Post by devin0 on 2009-07-03
I don't get any error message, it just shows the splash screen until I choose to close the terminal window. I would really like to get this program working, its the only program that is keeping me from using all linux software for my basic stamp.

As for what "michy99" said I will take a look at that program thank you for telling me about it.

---

### Post by devin0 on 2009-07-03
"You might find this helpful. It is written for KDE instead of Gnome, but you might be able to adapt it.

[http://www.gaess.ch/?page_id=5](http://www.gaess.ch/?page_id=5) "

This one looks like it would work great and do everything I want, but like you said its for kde. If anyone could tell me how to get it to work with gnome it would be great.

---

### Post by devin0 on 2009-07-03
I managed to get kate all set up, and its working just as good as the parallex one. Thanks :)

---

### Post by flybyspam on 2010-10-15
Will not compile.

Also,  Is there any guide to installing this without going through links that direct you to more links?   

   Per the guide on [http://www.gaess.ch/?page_id=5e](http://www.gaess.ch/?page_id=5e) that linked to download the tokenizer library at [http://bstamp.sourceforge.net/download/](http://bstamp.sourceforge.net/download/) and the link is "dead."  I found a tokenizer library on parallax's site and downloaded/extracted it.  But,  there  was no explanation about where to put the library at [http://www.gaess.ch/?page_id=5](http://www.gaess.ch/?page_id=5).  There's already a tokenizer.so that extracted with the bstamp-2006.05.31.tar.gz downloaded from [http://sourceforge.net/projects/bstamp/files/](http://sourceforge.net/projects/bstamp/files/).  **Am I supposed to overwrite it?**


   When following the README for installation:

Compiling:
----------
  You should simply be able to run "make" to compile the tools from source.

Installing:
-----------
  the following commands will allow you to install the bstamp utilities:

  Extract the bstamp program source code to a directory, and move into
  directory.

  > make clean
  > make
  > make install

These commands yield....big surprise....errors:  claiming no directories.
(yes the file has been extracted).

STAMP/bstamp# ls
bstamp_run.cpp       pbasic_examples
bstamp_tokenize.cpp  PBASIC_Tokenizer_Software_Distribution_License.pdf
CHANGES.txt          PBASIC_Tokenizer_Software_Distribution_License.txt
COPYING.txt          README.txt
error_handling.cpp   TODO.txt
GPL.txt              tokenizer.h
Makefile             tokenizer.so


  Getting frustrated with this.  Links to links that don't WORK.  I'm ready to give up to windows....at least i'll be able to program my PIC chips instead of spending hours following dead links.

by Bill Kendrick
[email]bill@newbreedsoftware.com[/email]
[http://www.newbreedsoftware.com](http://www.newbreedsoftware.com)

Brian Lavender
[email]brian@brie.com[/email]
[http://www.brie.com/brian/](http://www.brie.com/brian/)

Francis Esmonde-White
[email]francis@esmonde-white.com[/email]
[http://www.esmonde-white.com](http://www.esmonde-white.com)

---

