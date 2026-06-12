---
title: "Issuing commands in ubuntu"
date: 2012-03-11
forum: General Help
---

### Post by hares on 2012-03-11
Ok sorry again if this is in the wrong forum. literally my second day of unsing Linux. So far its been good. My major problem is issuing commands. i have no idea where to begin.

For example i've been trying to get a hack to work for diablo 2. After scouring forums and such I wound up reading on how to compile files.

Here's what the site says

If file extensions is .gz then use tar command as follows to extract tar ball:
 $ tar -zxvf file.tar.gz


Now: Where the heck do I put that command in!!!? I've read so much in Linux forums that i can probably compile programs and do alot of other stuff at this point, if I could get past the starting point of where to put commands in.

---

### Post by hares on 2012-03-11
Ok so i read some more into this. It says if I use a GUI (I use ubuntu, thus I'm assuming I use a GUI) it says look for shell prompt to issue commands in linux. I cant find where shell prompt is (how to open the basic commands section in linux..)

---

### Post by wojox on 2012-03-11
Use Ctrl + Alt + T keys to open a terminal.

---

### Post by houseworkshy on 2012-03-11
Or just use the mouse to open the terminal  (it's in the Applications menu) .  One nice thing about the command line is that it has its own built in help.  Typing "man" in front of any command will take you to a help page for that command, "man man" for example will tell you how that works.  When using this remember that you can have a lot of teminals open at the same time, which is handy as one can use one as a help window and another for typing commands.  You can also copy and paste between the two if you like.  

I'd recomend using,  um how to phrase it, diagnostic command first such as "list" rather than things which change things while you get the hang of it as it is one area where typing the wrong thing can mess up your system, be especially carefull of "sudo" as this grants temporary "root" powers.  Equally don't be afraid of it, I found it no harder than the old fashioned dos and rather more intuative.  

If feeling around for commands "apropos" is very useful as what that does is dig through the manuals and find referances to whatever word you typed after "apropos".  So "apropos search" would list commands which have the word search in the man pages to them.  Note all quotes in the above are only to seperate commands and not intended for entry.

There are also a lot of good guides, this one is exhaustive free and nicely written;
 
  [http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)

Also deepend so for something more basic, and not aimed soley at the command line but the gui too;

 [http://ubuntupocketguide.com/index_main.html](http://ubuntupocketguide.com/index_main.html)  Is good for an overview

There is also a lot of documentations on the main ubuntu site which is well worth browsing through.  Within that documentation are what are called apt;urls  these can be clicked to initialise an install.  So as a first step I'd recomend going through that.  It's mostly not about command lines but as you are new it is a very fast way of getting an overview and bunging in programs which you may like to have at the same time.  I'm not entirely happy about this method of installing elsewhere but trust the Ubuntu site itself.

Also because you are new I'd recomend using the 10.04 lts (long term support, three years actually and they overlap by a year so in theory one can always let the older one mature a year before swithching ) version of Ubuntu as it has had bugs ironed out of it, the six month releaces ( not lts ) often don't untill support for them has nearly run out.    You will see from the help forums that most of the problems refer to the 11's.   The  Its also uses the gnome desktop enviroment which has a beautiful intuitive simplicity;  my favorite gui ( graphic user interphase) ever.  I love the empty desktop background, it has a clean feeling somehow.  After the zenlike luxury of using it all the others feel cluttered, especially as one can do everything from it anyway. That's only my own aesthics of course.  There is a sticky at the head of the forums which tells you how to switch back to the gnome gui ( 11.10  uses a gui called ubiquity )  on later versions of ubuntu if you wish.  There are actually dozens of GUI's google for "+linux +GUI"  and you'll find lots.  I have more than one and choose at startup, sometimes it can be handy to use something very light on resorces if one wants to use a program/game which is heavy.  Its a bit like a nut, the kernal is the heart of the program which is machine codey stuff, the shell is wrapped around that and is human useable commands and the GUI is the graphic user interphase, menus, bars, things one can click with a mouse etc.  Everything which can be done in the GUI, and which doesn't depend on the gui ( which a few applications and games do ) can be done with commands.  A few things can only be done with commands.

Welcome to the forums btw.

Sorry not reading closely enough, you are not unfamiliar with linux.   Well the pdf  from the first link will take you up to expert anyway, superb book.  One thing about the book  though, there may still be a bit of advice about changing mouse behavior near the begining, I haven't re-downloaded to check.  I couldn't do  it, posted here and the author himself posted back saying that it was no longer valid so don't try.   All the rest is fine though.   I'll leave what I wrote up anyway as it may be useful to someone else sometime.

---

