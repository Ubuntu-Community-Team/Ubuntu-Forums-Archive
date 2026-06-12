---
title: "Broken Package"
date: 2006-01-26
forum: General Help
---

### Post by TechSonic on 2006-01-26
I've downloaded Skype and the deb package was broken when trying to load it.  Also a libqt file was also missing, I tried to find it on the update package tool, not able to find it.  I tried to get it with the QT already compiled, then the broken package update thing came up and went haywire once skype was actually running.  Then I just clicked to remove it via the package tool.

O.o

---

### Post by HJThis on 2006-01-26
Hello,TechSonic

Well one thing that has been a big help to me
installing new progs is this here

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

Best of luck:p

---

### Post by TechSonic on 2006-01-26
It may have been help to you, but in my case it's useless.  I'm not downloading something thats in the repository.


Let me explain..


skype:
 Depends: libqt3c102-mt (>=3:3.3.3.2) but it is not installable


The package that is in the respository is skype.  Thats what I'm trying to install.  But the package I need to install it is either missing or out of date.  From what I've found out, it's out of date.  libqt3c102-mt is an older version of what is already on my system.  I installed the new version in hopes it would work sense the old one wasn't installable.

And I've also found out why I get a haywire from the package manager when I try the already compiled with libqt3.  It sees it as bad mojo.

My next step is to see if I can compile it in my current (newer) version. Thats the last option I see left to try.

---

### Post by omegamike on 2006-01-27
A lot of people have had that problem with Skype (the missing libraries). If you have the libraries already installed through the Ubuntu repositories, then go to the Skype site and grab the Mandriva .rpm. You can use alien to install it, and it'll work like a charm. I set it up a day ago!

After downloading the rpm, crank up a terminal.

cd /to/where/you/saved/the/file
sudo apt-get install alien
sudo alien *name of .rpm*
sudo dpkg -i *the newly created .deb name*

obviously replace "*files*" with the actual file names

---

### Post by omegamike on 2006-01-27
Sorry, I wasn't clear on that. By libraries I meant the qt libraries. With the Mandriva .rpm, you can use the qt libraries that are installable with apt-get.

---

