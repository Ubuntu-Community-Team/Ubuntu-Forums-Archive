---
title: "How to install a software if *.bin is already available on local computer?"
date: 2010-06-22
forum: General Help
---

### Post by pstein on 2010-06-22
As I understand I can search for a software on Internet with apt-get resp. aptitude. These commands search automatically for the suitable install packages, retrieve them from remote (Internet) repositories and install them locally.
 
Fine so far.
 
But what if I have already the *.bin packages available on the local hard disc.
In such a case I need no search tool like apt-get or aptitude.
 
How do I just a simple install of a given *.bin?
 
Peter

---

### Post by bkline on 2010-06-22
Typically, you should be able to just execute the file: open a console window, navigate to the directory where you downloaded the file, type ./whatever.bin and answer the questions that come up.  You may need to do this with root permissions (sudo ./whatever.bin) or the installer for the software may give you the option to install the software privately in your own user area.  However, before you do any of this, you should be aware of some of the differences between launching an installer this way and using the standard Debian/Ubuntu package management tools:

[LIST=1]
[*]The likelihood of installing something malicious is greater if you bypass the standard package repositories. 
[*]The package management tools are able to take care of dependencies on other packages for you.
[*]Installing software outside the package management system makes it harder to keep your system updated.
[*]You need to have a more sophisticated understanding of how your system works in order to install software directly instead of using the package management system to do it for you (notice, for example, that I didn't explain above what I meant by "open a console window").
[/LIST]

If it sounds as if I'm trying to discourage you from installing software without using the package management tools provided with Ubuntu, that's because I am.  There are times when you don't have any other good options (for example, you need to use your system to do something for which there are no packages available), and I've done it myself.  You just want to be aware that it's not as good an option as you might think.

---

