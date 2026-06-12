---
title: "Compile lame.3.96.1 how to"
date: 2006-02-16
forum: General Help
---

### Post by JavaMain on 2006-02-16
Hallo

I have installed Kubuntu 3.10 and I require lame for the CD ripper (kAudioCreator I think) which is pre-installed. 

I have downloaded the lame 3.96.1 tar.gz but have no idea how to get from there to a working installed Lame encoder situation.

I have searched and only found some steps that extracted to a lame directory then said compile && make. But that failed :(

Thanx all

---

### Post by Greg2 on 2006-02-16
You can just install lame 3.96.1-1 or 3.97-0unofficial from the repositories with the package manager or apt-get.

However if you want to learn to compile apps I would suggest using the wiki how-tos:
[https://wiki.ubuntu.com/CompilingSoftware?highlight=%28CategoryDocumentation%29](https://wiki.ubuntu.com/CompilingSoftware?highlight=%28CategoryDocumentation%29)
[https://wiki.ubuntu.com/CompilingEasyHowTo?highlight=%28CategoryDocumentation%29](https://wiki.ubuntu.com/CompilingEasyHowTo?highlight=%28CategoryDocumentation%29)
and this:
[https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall)

---

### Post by xavierh on 2006-02-17
Where can you get lame 3.97 Beta? The repositories only have version 3.96.1

---

### Post by Greg2 on 2006-02-17
[QUOTE=xavierh]Where can you get lame 3.97 Beta? The repositories only have version 3.96.1[/QUOTE]It’s in the cipherfunk repo. Add [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main to your list. Here, use this to make it simple:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by xavierh on 2006-02-17
[QUOTE=Greg2]It’s in the cipherfunk repo. Add [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main to your list. Here, use this to make it simple:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)[/QUOTE]

Muchas pero muchas gracias Greg (Thanks so much Greg). This is another link that I need to add to my bookmarks

---

### Post by JavaMain on 2006-02-20
Thank you Greg2  - useful links - I didn't even know there was an ubuntu Wiki.

Answered a more general question of how to "Compile things on Ubuntu Linux the Easy Way" which gave me the sudo apt-get install build-essential answer I had needed. Plus other gems I only found thru tiresome Google groups searching.

Thanx again

---

### Post by nykobing on 2006-02-20
[QUOTE=xavierh]Where can you get lame 3.97 Beta? The repositories only have version 3.96.1[/QUOTE]

Lame 3.97 beta 1 is on [http://rarewares.org/mp3.html](http://rarewares.org/mp3.html), it works fine. I haven't seen a beta 2 yet though.

---

