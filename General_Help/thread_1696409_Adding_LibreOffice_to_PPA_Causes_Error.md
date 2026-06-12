---
title: "Adding LibreOffice to PPA Causes Error"
date: 2011-02-27
forum: General Help
---

### Post by MrRichard on 2011-02-27
A few minutes ago, I added LibreOffice's PPA to my sources list. When I went to update my computer, this popped up:
```
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'a.launchpad.net/libreoffice/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/libreoffice-ppa-maverick.list'
```

So I tried reporting this bug by tapping Alt+F2 and entering:
```
ubuntu-bug update-manager
```
Then an error pops up, saying it could not determining the package or source package name.

When I try clicking on Ubuntu Software Centre, nothing pops up :confused:

I'm really puzzled and would at least like to remove that LibreOffice PPA so I can use Ubuntu Software Centre.

---

### Post by sikander3786 on 2011-02-27
Please post the output of this command.

```
cat /etc/apt/sources.list.d/libreoffice-ppa-maverick.list
```

It is not really a bug but it is a typo in your libreoffice sources file. Hopefully, we'll spot it ;-)

---

### Post by MrRichard on 2011-02-27
```
# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu maverick main #Libreoffice PPA
a.launchpad.net/libreoffice/ppa/ubuntu maverick main

```
I believe that's all that popped out of the terminal :)

---

### Post by sikander3786 on 2011-02-27
Yes that is all contained in that file. I am not currently on my Ubuntu PC and can't find a libreoffice-ppa-maverick.list for you sadly.

What we can do and that will work equally well is to go to Software Center > Edit > Software Sources > Other Software Tab and disable all the Libreoffice PPAs.

Now go to Terminal and do follow the commands from this page.

[http://ubuntu4beginners.blogspot.com/2011/02/install-libreoffice-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/install-libreoffice-in-ubuntu.html)

Good Luck!

---

### Post by MrRichard on 2011-02-27
Hehe, that was the same tutorial that got me into this mess :)

It turns out that I had to delete two files under /etc/apt/sourses.list.d/ that were related to a different LibreOffice ppa (or something like that). Now the tutorial works perfectly. Thanks for the help!

---

