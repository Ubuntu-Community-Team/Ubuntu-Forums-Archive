---
title: "Best GUI interface program for ripping DVD??"
date: 2006-02-25
forum: General Help
---

### Post by MJSOnline on 2006-02-25
Hi all.  What is the best, or close to the best GUI program to rip DVD's??  What apps and codecs do I need to do this?  Or just a front end to a terminal program? What apps will then read the files and burn them to a new DVD? Would the files be vob's?  Thanks.  Matthew

---

### Post by MJSOnline on 2006-02-25
[QUOTE=MJSOnline]Hi all.  What is the best, or close to the best GUI program to rip DVD's??  What apps and codecs do I need to do this?  Or just a front end to a terminal program? What apps will then read the files and burn them to a new DVD? Would the files be vob's?  Thanks.  Matthew[/QUOTE]
Anyone?  M

---

### Post by BeatBoxRocker on 2006-02-25
DVD::rip i think is the best program available to rip DVDs.

Saludos!

---

### Post by aysiu on 2006-02-25
[QUOTE=BeatBoxRocker]DVD::rip i think is the best program available to rip DVDs.[/QUOTE] [Here's a screenshot from the program's homepage](http://www.exit1.org/dvdrip/doc/img/shots/clip_zoom.png).

---

### Post by oscar on 2006-02-25
I like and have used acidrip, I have not tried DVD:rip.

---

### Post by MJSOnline on 2006-02-25
Ok.  How do I install dvd::rip?  M

---

### Post by jobezone on 2006-02-25
Try thoggen! [http://thoggen.net/](http://thoggen.net/)
It's still a bit slow on the ripping part, but it's the best and easiest interface for ripping. Unfortunatelly, the newest version hasn't got a .deb yet.. Maybe ubuntu backports people have it packaged already?
Screenshots: [http://thoggen.net/screenshots/](http://thoggen.net/screenshots/)

EDIT: I think it's in the Universe repository, see if it is. Do:
```
sudo apt-get install thoggen
``` in a terminal.

---

### Post by MJSOnline on 2006-02-25
[QUOTE=jobezone]Try thoggen! [http://thoggen.net/](http://thoggen.net/)
It's still a bit slow on the ripping part, but it's the best and easiest interface for ripping. Unfortunatelly, the newest version hasn't got a .deb yet.. Maybe ubuntu backports people have it packaged already?
Screenshots: [http://thoggen.net/screenshots/](http://thoggen.net/screenshots/)

EDIT: I think it's in the Universe repository, see if it is. Do:
```
sudo apt-get install thoggen
``` in a terminal.[/QUOTE]

Ok,  but I did see this before buti I could not see it using in gui mode.  How do I install it?  Run it? I can't see it in my applications drop down list.. Any help would be good.  Thanks. M

---

### Post by MJSOnline on 2006-02-25
How do I install DVD::rip?  M

---

### Post by BeatBoxRocker on 2006-02-25
This is the page of [DVD::rip]("http://www.exit1.org/dvdrip/"), take a look at the page for info and docs. 

To download program and documentation: sudo apt-get install dvdrip dvdrip-doc

Maybe you will like to use a newer version, you can find it in the Christian Marillat repositories. Add this line to sources.list but i recommend you to comment the line after the program is installed in your system:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sid main

Saludos!

---

### Post by sean.smithson on 2006-02-26
snip

---

### Post by MJSOnline on 2006-02-26
Hi all.  I have downloaded DVD::rip and trying to install it using the docs on the DVD::rip web site, but I get this error when I do a "make test"

[B]matthew@Main:/media/SlaveDrive/DLoads/Video-DVDRip-0.52.6$ make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-Iblib/lib" "-Iblib/arch" test.pl
1..1
[filterlist] (re)scanning transcode's module path /usr/lib/transcode...
sh: line 1: 11051 Segmentation fault      tcmodinfo -i compare 2>/dev/null
ok 1 - load dvd::rip
matthew@Main:/media/SlaveDrive/DLoads/Video-DVDRip-0.52.6$[/B]

What does it mean and how do I fix it so I can install DVD::rip?  Thanks. M

---

### Post by MJSOnline on 2006-02-27
Anyone got any ideas?  What am I missing?  Thanks in advance.  M

---

### Post by lha on 2006-02-27
DVD::Rip is in multiverse, is there a reason why don't want to use it? (The package is called dvdrip.)

---

### Post by jobezone on 2006-02-27
[QUOTE=MJSOnline]Anyone got any ideas?  What am I missing?  Thanks in advance.  M[/QUOTE]
Oh, and if you installed thoggen, but don't have it in the menu, you can still launch it:
press ALT+F2
write **thoggen** and
press enter

The reason it did not get into the menu, is that that the developer for the software hasn't made one yet. Or, you could edit your menu, and see if it's hidden (Right click on Aplications, and choose Edit Menus).

---

### Post by maumar on 2006-03-01
I´ve installed thoggen and I have installed libdvdcss2 (version 1.2.8-1unofficialubuntu3) but when ever I try to rip a DVD I get the message:

Could not read DVD Title. Is libdvdcss2 installed?

What can I do to solve this problem?

In the shell I get following message:
...
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can´t open /dev/dvd for reading

Thanxs Martin

---

