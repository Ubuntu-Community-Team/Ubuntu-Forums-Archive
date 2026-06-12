---
title: "Some questions from an absolute beginer=-)"
date: 2011-09-01
forum: General Help
---

### Post by Teolaren on 2011-09-01
Hi, all)
Let me introduce myself)
First, i' m terribly sorry for my english) 
As i wrote, i'm a total  beginner in computer using art, so i am sometimes unaware of the very  simple things and it's difficult to explain them in english, it is foreign for me and i may  use some incorrect words %)
My laptop is an Asus 1215n. I like it much) After three months of quite happy using it with Windows, i ran into a problem: touchpad got crazy. First, i thought it was the system problem - and tried to solve it with some bios magic - which didn't work.
Then, my friend told me about Linux and made me totaly in love with it. I've read something about ( particularly here [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)) and decided to try. My friend gave me ubuntu's life-CD, which  run on my laptop during three days, and the touchpad worked too. So we decided to move, and have moved to the 11.4 Natty Narwhal. 
Actually, touchpad problems didn't move away so simple - i had to dismantle my laptop a little - anyway it is working good now.
BUT, i'm am an ubuntu user, i hope not to come back to windows, because i like the way ubuntu looks and the way it works even if i don't understand some (oh, honestly - MANYMANY) things about. I would like to learn)
Finally (thank you for being patient enought to read till here) i have some questions)
First is about kchmViewer. 
Here :
[http://www.linux.com/news/software/applications/8209-chm-viewers-for-linux](http://www.linux.com/news/software/applications/8209-chm-viewers-for-linux)
i found the description of some progs which could help me to read my histology manual which is an chm file, and i choosed to install the kchmviewer. Followed the link till here
[http://www.kchmviewer.net/download.html](http://www.kchmviewer.net/download.html)
read infos about. downloaded the latest version. checked the qt4-devel and chmlib-devel packages installation with synaptic package manager, unpacked the downloaded archive and never found readme file inside %|
It is quite possible i'm too much stupid, but i'm utterly puzzled over..
Second one, 
on the panel, where "applications","places" and other useful things are always waiting, just behind A- P- S divisions' names the are some strange striae looks like if panel once was horizontal and in the middle of the screen, and left it's ghostly trace but it never was.. Is it possible to remove it?

Thank you so much for your attention and for any help)

---

### Post by searchfgold6789 on 2011-09-01
Hi,
I think Ubuntu can install using .rpm files. Try this file to automatically install the viewer:```
http://sourceforge.net/projects/kchmviewer/files/kchmviewer/5.3/kchmviewer-5.3-1.i586.rpm/download
```If that doesn't work, you can use the README file here:```
http://sourceforge.net/projects/kchmviewer/files/kchmviewer/5.3/README/download
```The README is not in the archive, it's on the download website in the appropriate directory.
As for your panel issue, can you provide a screenshot?

---

### Post by sauerpauer on 2011-09-01
Learning how to install .rpm files on Ubuntu would be more trouble than it is worth, so I would definitely recommend downloading the .tar.gz file from [http://sourceforge.net/projects/kchmviewer/files/kchmviewer/5.3/]("http://sourceforge.net/projects/kchmviewer/files/kchmviewer/5.3/").  Then, just double click the file, and it should be unpacked for you automatically.

As for the dependencies "qt4-devel" and "chmlib-devel", I'm not sure if they are included, so you may have to get these from a different place.

As for the panel, if you right-click the menu and select "edit menus" you might be able to fix the problem yourself.  Be careful though, that panel can be a pain to deal with, so if you can't figure it out post a screenshot here.

---

### Post by oldos2er on 2011-09-01
Copy and paste this in a terminal ```
sudo apt-get update && sudo apt-get install kchmviewer
```

---

