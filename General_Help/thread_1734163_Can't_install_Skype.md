---
title: "Can't install Skype"
date: 2011-04-19
forum: General Help
---

### Post by Arashikage on 2011-04-19
I try to install Skype on my laptop(Ubuntu 11.04) but it keeps saying "The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath. 
Lintian check results for /tmp/skype-ubuntu_2.2.0.25-1_i386.deb:
E: skype: description-starts-with-package-name 
W: skype: extended-description-line-too-long 
W: skype: extended-description-line-too-long 
W: skype: possible-unindented-list-in-extended-description 
W: skype: new-package-should-close-itp-bug 
W: skype: binary-without-manpage usr/bin/skype "

The same type of thing happened when I tried to install pidgin, but I have it installed now through the terminal.  Is there a terminal command I can use to get Skype?  Or is there a place I can put the dynamic files I downloaded?  Help is appreciated, thanks.

---

### Post by earthpigg on 2011-04-19
hi,

have you checked the 'software center' for skype?

make sure you go to edit -> software sources first, and check some boxes.

alternatively, you can do:

sudo dpkg -i /path/to/skype-ubuntu_2.2.0.25-1_i386.deb

---

### Post by Arashikage on 2011-04-20
I checked the software center, and there is no skype on the list, I tried going to edit -> software sources, but no such option exists in the software center.  I tried the terminal code as well, and it said "Cannot access archive: No such file or directory"

I have the dynamic files, if there's a place I can put them, I could just put them in there and it will work, right?

---

### Post by ashickur.noor on 2011-04-20
> **Arashikage said:**
> I checked the software center, and there is no skype on the list, I tried going to edit -> software sources, but no such option exists in the software center.  I tried the terminal code as well, and it said "Cannot access archive: No such file or directory"

I have the dynamic files, if there's a place I can put them, I could just put them in there and it will work, right?
User Super [Os Repo.]("http://hacktolive.org/files/Super_OS_10.04_repo_v0.3.1_all.deb")

Install this *.deb file, update your source. Then you can have skype if skype is avail for 11.04

---

### Post by earthpigg on 2011-04-21
> **ashickur.noor said:**
> User Super [Os Repo.]("http://hacktolive.org/files/Super_OS_10.04_repo_v0.3.1_all.deb")

Install this *.deb file, update your source. Then you can have skype if skype is avail for 11.04

erm, please don't install that .deb until visiting the [website of the folks that published it]("http://hacktolive.org/wiki/Super_OS") and deciding yourself that you trust them. that is how malware can be spread (yes, even on linux.).

> I tried going to edit -> software sources, but no such option exists in the software center. I tried the terminal code as well, and it said "Cannot access archive: No such file or directory"
 

I should have been more clear. Edit -> Software Sources -> Other Software -> Canonical Partners.

if that doesn't do it, then back to the terminal telling you:
> "Cannot access archive: No such file or directory"
can you please copy/paste exactly what you typed, and share the full/exact path to where you have the skype .deb downloaded to?


> I have the dynamic files, if there's a place I can put them, I could just put them in there and it will work, right?

nono, please do not do that.

---

### Post by HermanAB on 2011-04-21
Note that you can install the 'static' version of Skype from the Skype web site.  That version is statically linked and contains all required libraries in the package, so it pretty much always works.

---

### Post by enarsee on 2011-04-21
As the guy above said,

Here is the link :)

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

