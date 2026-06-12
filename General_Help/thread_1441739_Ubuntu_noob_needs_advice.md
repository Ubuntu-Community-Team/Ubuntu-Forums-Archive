---
title: "Ubuntu noob needs advice"
date: 2010-03-29
forum: General Help
---

### Post by Shadow1like on 2010-03-29
:rolleyes:I apologize for asking such a "nooby" question, but I am also a Windows user and this is my first time experimenting with Ubuntu.

That being said I have a dumb question or questions how ever you want to look at it.

Does Ubuntu need any type of Maintenance?(dumb question......... sorry) and if so What "FREE" programs could be used together to be a complete suite to keep my system purring away happily?

oh yeah and what free anti-virus should I have?

---

### Post by Wrinkliez on 2010-03-29
if you mean something like CCleaner for windows... there really isn't anything like that for linux (it doesn't need it). I suppose if you installed something and you wanted to get rid of the dependencies, you could type "sudo apt-get autoremove" in the terminal.

Or you could click System > Administration > Computer Janitor to keep it clean (this has been debated... some people say it removes things that shouldnt be removed).  I don't use it regularly, but I have used it before and nothing bad happened.

And you don't need an antivirus for linux.  Anyone who tries to sell one to you is juts trying to make money.  The OS is open source, so it's incredibly difficult to get viruses going.

---

### Post by derekeverett on 2010-03-29
As long as you keep doing your updates and install apps and packages only through the repositories you should be fine.

After you've adjusted some to how things work you can start looking at adding additional repos and installing via other methods.. but it's seldom the case that has to be done.

Just don't be afraid to ask questions and certainly spend some time seeking answers and reading the documentation.

Patience is very important. Most of this stuff isn't hard but a fair amount of it is probably different from what your used to.

Most people that freak out in here and quit Ubuntu do so because they lacked patience and couldn't get everything the way they liked it in half an hour.

---

### Post by 3rdalbum on 2010-03-29
> **Shadow1like said:**
> :rolleyes:I apologize for asking such a "nooby" question, but I am also a Windows user and this is my first time experimenting with Ubuntu.

That being said I have a dumb question or questions how ever you want to look at it.

They're not dumb questions. Don't worry about that :-)

> Does Ubuntu need any type of Maintenance?(dumb question......... sorry) and if so What "FREE" programs could be used together to be a complete suite to keep my system purring away happily?

Maintenance consists entirely of running your system updates in Update Manager. Every thirty boots, your disk will be checked for errors, and fixed if necessary - but this is automatic.

> oh yeah and what free anti-virus should I have?

Welcome to Linux - you don't need anti-virus, there are no Linux viruses at the present. There haven't been for a while actually. You do sometimes have to be careful with what you install outside the repositories; for instance, stick to well-known PPAs (repositories) and the occasional well-known software manufacturer site (Skype.net, Opera.com, that sort of thing).

A while back there was a "screensaver" posted to the gnome-look.org website that was actually malware, but it required you to actually install it via Debian package. Ubuntu's package installer gives you the ability to inspect the contents of a package before installing it - once you get a feeling for where things go in the Linux filesystem, you'll be able to see if the package's contents are suspicious. (for instance, a "game" would not put files into the startup system).

---

### Post by maverick77_uk on 2010-03-29
Hiya,

Being an Ubuntu and Windows user, Ubuntu is a breeze when it comes to maintenance relative to Windows.  As people have said, make sure you're up-to-date (automatic).  You're supported for 18 months (standard release) or 3 years (Long Term release (LTS)), of which the up and coming 10.04 is the next LTS.

If you want to run an anti-virus because you'll be passing files to a Windows PC and want to check them, CLAM is pretty good, and has a GUI (user interface).  This can be installed from the synampic or package-manager-of-choice.


-------------------------------------------------------------------------------------
[http://www.biocomp.co.uk](http://www.biocomp.co.uk)

---

